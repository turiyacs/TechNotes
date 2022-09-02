## Install

```bash
setx ChocolateyInstall D:\Choco

Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser

iwr https://chocolatey.org/install.ps1 -UseBasicParsing | iex
```

* Copy config msbuild.rsp, Edge.json, MyBuild.dll

## Moving

```bash
setx ChocolateyInstall D:\Choco

ADD TO PATH D:\Choco\bin;D:\Choco\portable\MyCSApp;D:\Choco\portable\OnPath
```

## Installs

* cake.portable

## Apps

* __Apps__ : Folder for all shortcuts
* __CarotDav__ : portable install
* __Cmder__ : copy 'user-aliases.cmd'
* __DevTools__ : copy this package
* __FreeFileSync__ : portable install
* __GoogleChromePortable__ : portable install
* __Greenshot__ : custom version
* __ILSpy__ : disable auto update
* __IrfanView__ : custom version with package and plugins
* __MyCSApp__ : copy this package
* __MySystem__ : copy this package
* __QuiteRSS__ : portable install
* __Todomoo__ : custom version with ILMerge
* __WinMerge__ : portable install
