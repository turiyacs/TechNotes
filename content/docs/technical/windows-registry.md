---
weight: 2
title: Windows Registry
bookToc: false
---

# Windows Registry

## Disable Strong Name Validation Requirement

``` reg
REG DELETE "HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\StrongName\Verification" /f
REG ADD "HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\StrongName\Verification\*,*" /f
REG DELETE "HKEY_LOCAL_MACHINE\Software\Microsoft\StrongName\Verification" /f
REG ADD "HKEY_LOCAL_MACHINE\Software\Microsoft\StrongName\Verification\*,*" /f
```

## Windows Startup programs

``` reg
HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run
```
