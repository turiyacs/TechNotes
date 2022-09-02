## PowerShell

### Setting environment variables.

```powershell
$PATH = [Environment]::GetEnvironmentVariable("PATH")
$extra = "D:\Choco\bin;D:\Choco\portable\MyCSApp;D:\Choco\portable\OnPath"
[Environment]::SetEnvironmentVariable("PATH", "$PATH;$extra", "User")
```
