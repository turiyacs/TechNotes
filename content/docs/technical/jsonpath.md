## JSONPath - XPath for JSON

A frequently emphasized advantage of XML is the availability of plenty tools to analyse, transform and selectively extract data out of XML documents. [XPath](http://en.wikipedia.org/wiki/XPath) is one of these powerful tools.

It's time to wonder, if there is a need for something like XPath4JSON and what are the problems it can solve.

* Data may be interactively found and extracted out of [JSON](http://json.org) structures on the client without special scripting.
* JSON data requested by the client can be reduced to the relevant parts on the server, such minimizing the bandwidth usage of the server response.

If we agree, that a tool for picking parts out of a JSON structure at hand does make sense, some questions come up. How should it do its job? How do JSONPath expressions look like?

Due to the fact, that JSON is a natural representation of data for the C family of programming languages, the chances are high, that the particular language has native syntax elements to access a JSON structure.

The following XPath expression

`/store/book[1]/title`

would look like

`x.store.book[0].title`

or

`x['store']['book'][0]['title']`

in Javascript, Python and PHP with a variable `x` holding the JSON structure. Here we observe, that the particular language usually has a fundamental XPath feature already built in.

The JSONPath tool in question should .

* be naturally based on those language characteristics.
* cover only essential parts of XPath 1.0.
* be lightweight in code size and memory consumption.
* be runtime efficient.

### JSONPath expressions

JSONPath expressions always refer to a JSON structure in the same way as XPath expression are used in combination with an XML document. Since a JSON structure is usually anonymous and doesn't necessarily have a "root member object" JSONPath assumes the abstract name $ assigned to the outer level object.

JSONPath expressions can use the _dot_-notation

`$.store.book[0].title`

or the _bracket_-notation

`$['store']['book'][0]['title']`

for input pathes. Internal or output pathes will always be converted to the more general _bracket_-notation.

JSONPath allows the _wildcard_ symbol * for member names and array indices. It borrows the _descendant_ operator '..' from [E4X](http://en.wikipedia.org/wiki/E4X) and the _[array slice syntax](http://developer.mozilla.org/es4/proposals/slice_syntax.html)_ proposal `[start:end:step]` from [ECMASCRIPT 4](http://www.ecmascript.org/).

Expressions of the underlying scripting language `(<expr>)` can be used as an alternative to explicit names or indices as in

`$.store.book[(@.length-1)].title`

using the symbol '@' for the current object. Filter expressions are supported via the syntax `?(<boolean expr>)` as in

`$.store.book[?(@.price < 10)].title`

Here is a complete overview and a side by side comparison of the JSONPath syntax elements with its XPath counterparts.

| **XPath** | **JSONPath**     | **Description**                                                                                                                                   |
| --------- | ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| /         | $                | the root object/element                                                                                                                           |
| .         | @                | the current object/element                                                                                                                        |
| /         | . or []          | child operator                                                                                                                                    |
| ..        | n/a              | parent operator                                                                                                                                   |
| //        | ..               | recursive descent. JSONPath borrows this syntax from E4X.                                                                                         |
| *         | *                | wildcard. All objects/elements regardless their names.                                                                                            |
| @         | n/a              | attribute access. JSON structures don't have attributes.                                                                                          |
| []        | []               | subscript operator. XPath uses it to iterate over element collections and for predicates. In Javascript and JSON it is the native array operator. |
| \|        | [,]              | Union operator in XPath results in a combination of node sets. JSONPath allows alternate names or array indices as a set.                         |
| n/a       | [start:end:step] | array slice operator borrowed from ES4\.                                                                                                          |
| []        | ?()              | applies a filter (script) expression.                                                                                                             |
| n/a       | ()               | script expression, using the underlying script engine.                                                                                            |
| ()        | n/a              | grouping in Xpath                                                                                                                                 |

XPath has a lot more to offer (Location pathes in not abbreviated syntax, operators and functions) than listed here. Moreover there is a remarkable difference how the subscript operator works in Xpath and JSONPath.

* Square brackets in XPath expressions always operate on the _node set_ resulting from the previous path fragment. Indices always start by 1.
* With JSONPath square brackets operate on the _object_ or _array_ addressed by the previous path fragment. Indices always start by 0\.

### JSONPath examples

Let's practice JSONPath expressions by some more examples. We start with a simple JSON structure built after an XML example representing a bookstore (original [XML file](http://coli.lili.uni-bielefeld.de/~andreas/Seminare/sommer02/books.xml)).

``` json
{ "store": {
    "book": [
      { "category": "reference",
        "author": "Nigel Rees",
        "title": "Sayings of the Century",
        "price": 8.95
      },
      { "category": "fiction",
        "author": "Evelyn Waugh",
        "title": "Sword of Honour",
        "price": 12.99
      },
      { "category": "fiction",
        "author": "Herman Melville",
        "title": "Moby Dick",
        "isbn": "0-553-21311-3",
        "price": 8.99
      },
      { "category": "fiction",
        "author": "J. R. R. Tolkien",
        "title": "The Lord of the Rings",
        "isbn": "0-395-19395-8",
        "price": 22.99
      }
    ],
    "bicycle": {
      "color": "red",
      "price": 19.95
    }
  }
}
```

| **XPath**              | **JSONPath**                           | **Result**                                                   |
| ---------------------- | -------------------------------------- | ------------------------------------------------------------ |
| `/store/book/author`   | `$.store.book[*].author`               | the authors of all books in the store                        |
| `//author`             | `$..author`                            | all authors                                                  |
| `/store/*`             | `$.store.*`                            | all things in store, which are some books and a red bicycle. |
| `/store//price`        | `$.store..price`                       | the price of everything in the store.                        |
| `//book[3]`            | `$..book[2]`                           | the third book                                               |
| `//book[last()]`       | `$..book[(@.length-1)]` `$..book[-1:]` | the last book in order.                                      |
| `//book[position()<3]` | `$..book[0,1]` `$..book[:2]`           | the first two books                                          |
| `//book[isbn]`         | `$..book[?(@.isbn)]`                   | filter all books with isbn number                            |
| `//book[price<10]`     | `$..book[?(@.price<10)]`               | filter all books cheapier than 10                            |
| `//*`                  | `$..*`                                 | all Elements in XML document. All members of JSON structure. |
