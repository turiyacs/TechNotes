# Windows

## Registry

## Locations

* Hosts file `C:\Windows\System32\drivers\etc\hosts`

## Group Policy

* Symbolic Links: `Computer Configuration\Windows Settings\Security Settings\Local Policies\User Rights Assignment\Create symbolic links`

## System

* ```shell:quick launch```

## Windows Startup Programs

* `%AppData%\Roaming\Microsoft\Windows\Start Menu\Programs\Startup` aka `shell:startup`
* `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Run`
* `C:\ProgramData\Microsoft\Windows\Start Menu\Programs\StartUp` aka `shell:common startup`

``` txt
%AppData%\Microsoft\Windows\Start Menu\Programs\Startup

[HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Run]
[HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\RunOnce]
[HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\RunServices]
[HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\RunServicesOnce]
[HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Winlogon\Userinit]

[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run]
[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\RunOnce]
[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\RunServices]
[HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\RunServicesOnce]
[HKEY_CURRENT_USER\Software\Microsoft\Windows NT\CurrentVersion\Windows]
```

## Shell Short Cuts

### Windows XP

``` txt
shell:Common Programs
shell:Favorites
shell:My Video
shell:System
shell:CommonVideo
shell:LocalizedResourcesDir
shell:Cookies
shell:My Pictures
shell:Cache
shell:AppData
shell:My Music
shell:InternetFolder
shell:Profile
shell:Start Menu
shell:Common AppData
shell:ConnectionsFolder
shell:Administrative Tools
shell:PrintersFolder
shell:ProgramFiles
shell:Common Startup
shell:ControlPanelFolder
shell:SendTo
shell:ResourceDir
shell:ProgramFiles
shell:PrintHood
shell:CD Burning
shell:Common Start Menu
shell:Templates
shell:Programs
shell:Recent
shell:Desktop
shell:CommonPictures
shell:RecycleBinFolder
shell:Common Templates
shell:Startup
shell:Common Desktop
shell:NetHood
shell:Common Administrative Tools
shell:SystemX86
shell:History
shell:Common Documents
shell:Local AppData
shell:Windows
shell:Fonts
shell:Personal
```

### Windows Vista

``` txt
shell:Common Programs
shell:GameTasks
shell:UserProfiles
shell:MyComputerFolder
shell:SyncSetupFolder
shell:DpapiKeys
shell:SamplePlaylists
shell:Favorites
shell:My Video
shell:SearchHomeFolder
shell:System
shell:CommonVideo
shell:SyncResultsFolder
shell:LocalizedResourcesDir
shell:Cookies
shell:Original Images
shell:CommonMusic
shell:My Pictures
shell:Cache
shell:Downloads
shell:CommonDownloads
shell:AppData
shell:SyncCenterFolder
shell:My Music
shell:ConflictFolder
shell:SavedGames
shell:InternetFolder
shell:Quick Launch
shell:SystemCertificates
shell:Contacts
shell:TreePropertiesFolder
shell:Profile
shell:Start Menu
shell:Common AppData
shell:PhotoAlbums
shell:ConnectionsFolder
shell:Administrative Tools
shell:PrintersFolder
shell:Default Gadgets
shell:ProgramFilesX86
shell:Searches
shell:Common Startup
shell:ControlPanelFolder
shell:SampleVideos
shell:SendTo
shell:ResourceDir
shell:ProgramFiles
shell:CredentialManager
shell:PrintHood
shell:MAPIFolder
shell:CD Burning
shell:AppUpdatesFolder
shell:Common Start Menu
shell:LocalAppDataLow
shell:Templates
shell:Gadgets
shell:Programs
shell:Recent
shell:SampleMusic
shell:Desktop
shell:CommonPictures
shell:RecycleBinFolder
shell:CryptoKeys
shell:Common Templates
shell:Startup
shell:Links
shell:OEM Links
shell:SamplePictures
shell:Common Desktop
shell:NetHood
shell:Games
shell:Common Administrative Tools
shell:NetworkPlacesFolder
shell:SystemX86
shell:History
shell:AddNewProgramsFolder
shell:Playlists
shell:ProgramFilesCommonX86
shell:PublicGameTasks
shell:ChangeRemoveProgramsFolder
shell:Public
shell:Common Documents
shell:CSCFolder
shell:Local AppData
shell:Windows
shell:UsersFilesFolder
shell:ProgramFilesCommon
shell:Fonts
shell:Personal
```

### Windows 7

``` txt
shell:Libraries
shell:MusicLibrary
shell:VideosLibrary
shell:OtherUsersFolder
shell:Device Metadata Store
shell:PublicSuggestedLocations
shell:SuggestedLocations
shell:RecordedTVLibrary
shell:UserProgramFiles
shell:DocumentsLibrary
shell:User Pinned
shell:UsersLibrariesFolder
shell:PicturesLibrary
shell:ImplicitAppShortcuts
shell:UserProgramFilesCommon
shell:Ringtones
shell:CommonRingtones
```
