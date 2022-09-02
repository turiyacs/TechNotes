## Git Notes

| Work                          | Command                                |
| ----------------------------- | -------------------------------------- |
| Shrink repository size        | `git reflog expire --all --expire=now` |
|                               | `git gc --prune=now --aggressive`      |
| Rebase Last N commits         | `git rebase -i HEAD~X`                 |
| Rebase including first commit | `git rebase -i --root`                 |
| Remove a branch on server     | `git push origin --delete dev`         |
| Set upstream branch           | `git push --set-upstream origin dev`   |
| Merge without commit          | `git merge <branch> --squash`          |
| List all git repository urls  | `grep -inr url --include config`       |
| Create a patch                | `git format-patch -n HEAD^`            |

1. Sparse Checkout

    `git config core.sparsecheckout true`

    ```
    /*
    !Files to ignore
    ```

6. Pull only master
    ```
    [remote "origin"]
    fetch = +refs/heads/master:refs/remotes/origin/master
    fetch = +refs/heads/my*:refs/remotes/origin/my*
    ```

7. Work Trees

    ```
    git worktree add -b emergency-fix ../temp master
    git worktree prune | list
    ```

### How to make bare repository to work normally?

* Copy entire stuff to .git under new empty directory.
* remove `bare = true`
* Add following lines

    ``` text
    [branch "master"]
        remote = origin
        merge = refs/heads/master
    ```

### Git create branch from older commit

    > `git branch branchname <sha1-of-commit>`
    > `git branch branchname HEAD~3`

### Get list of repositories?

    `dir .git /b/s /a:h`

### Git change committed user name

    `git commit --amend --author "New Author Name <email@address.com>"`

```bash
#!/bin/sh

git filter-branch --env-filter '
OLD_EMAIL="your-old-email@example.com"
CORRECT_NAME="Your Correct Name"
CORRECT_EMAIL="your-correct-email@example.com"
if [ "$GIT_COMMITTER_EMAIL" = "$OLD_EMAIL" ]
then
    export GIT_COMMITTER_NAME="$CORRECT_NAME"
    export GIT_COMMITTER_EMAIL="$CORRECT_EMAIL"
fi
if [ "$GIT_AUTHOR_EMAIL" = "$OLD_EMAIL" ]
then
    export GIT_AUTHOR_NAME="$CORRECT_NAME"
    export GIT_AUTHOR_EMAIL="$CORRECT_EMAIL"
fi
' --tag-name-filter cat -- --branches --tags
```

### Commands Comparison

| Command                     | Git                     | TFS                                                         |
| --------------------------- | ----------------------- | ----------------------------------------------------------- |
| Latest Change Set on Client | `git rev-parse HEAD`    | `tf history . /r /noprompt /stopafter:1 /version:W`         |
| Sync to a particular Change | `git reset --hard HASH` | `tf.exe get c:\tfs\  /version:c<NUMBER>  /force /recursive` |
|                             |                         |                                                             |
