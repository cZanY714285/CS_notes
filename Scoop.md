# What is Scoop?

Scoop is a command-line installer for Windows that simplifies the process of **installing software and managing packages**. It is similar to package managers in Linux, such as `apt` (for Debian-based systems) or `yum` (for RedHat-based systems), but designed specifically for Windows. The goal of Scoop is to make **managing software easier** by automating installations and keeping everything in one place.

Instead of searching for a download link, downloading an installer, running it, and clicking through a setup wizard, you can install software with a single command.
# References
1. [官方文档](https://github.com/ScoopInstaller/Scoop)
2. [quick start](https://github.com/ScoopInstaller/Scoop/wiki/Quick-Start)
3. [csdiy](https://csdiy.wiki/%E5%BF%85%E5%AD%A6%E5%B7%A5%E5%85%B7/Scoop/)
# Install Scoop Itself
## step 1: install PowerShell 7 for Windows

1. Open PowerShell in Windows. By default, Windows 10 restricts the execution of PowerShell scripts for security reasons.
2. You will see a red warning message with a link to: [[https://aka.ms/pswindows](https://aka.ms/pswindows)].
3. Visit the above link, which redirects to the PowerShell migration guide: [Microsoft Docs - Migrating to PowerShell 7](https://learn.microsoft.com/en-us/powershell/scripting/whats-new/migrating-from-windows-powershell-51-to-powershell-7?view=powershell-7.4).
4. Click "Installing PowerShell 7 (x64)", choose to download MSI package and ZIP package. here i chose MSI package.
5. then all you need is to follow the instruction.
## step 2: install Scoop in PowerShell terminal

1. this is what you can see in your powershell terminal:
```powershell
PS C:\Users\<YOUR USER NAME>
```
2. then you need to type this:
```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
Invoke-RestMethod -Uri https://get.scoop.sh | Invoke-Expression
```
3. and here's the output you can see:
```powershell
Initializing...
Downloading...
Creating shim...
Adding ~\scoop\shims to your path.
Scoop was installed successfully!
```
It will install Scoop to its default location:`C:\Users\YOUR NAME\scoop`
# Key Commands for Using Scoop
## use `scoop help` for instructions
- here's the output after you type `scoop help`:
```powershell
Usage: scoop <command> [<args>]

Available commands are listed below.

Type 'scoop help <command>' to get more help for a specific command.

Command    Summary
-------    -------
alias      Manage scoop aliases
bucket     Manage Scoop buckets
cache      Show or clear the download cache
cat        Show content of specified manifest.
checkup    Check for potential problems
cleanup    Cleanup apps by removing old versions
config     Get or set configuration values
create     Create a custom app manifest
depends    List dependencies for an app, in the order they'll be…
download   Download apps in the cache folder and verify hashes
export     Exports installed apps, buckets (and optionally confi…
help       Show help for a command
hold       Hold an app to disable updates
home       Opens the app homepage
import     Imports apps, buckets and configs from a Scoopfile in…
info       Display information about an app
install    Install apps
list       List installed apps
prefix     Returns the path to the specified app
reset      Reset an app to resolve conflicts
search     Search available apps
shim       Manipulate Scoop shims
status     Show status and check for new app versions
unhold     Unhold an app to enable updates
uninstall  Uninstall an app
update     Update apps, or Scoop itself
virustotal Look for app's hash or url on virustotal.com
which      Locate a shim/executable (similar to 'which' on Linux)
```
## install a program
### the form of input:
```powershell
scoop install NAME
```
### following are some examples:
#### install aria2
Scoop uses 'aria2c' for multi-connection downloads. So after you download this, it will be used for all downloads afterward.
1. your input
```powershell
scoop install aria2
```
2. the output
```powershell
Installing 'aria2' (1.37.0-1) [64bit] from 'main' bucket
aria2-1.37.0-win-64bit-build1.zip (2.4 MB) [==================================================================] 100%
Checking hash of aria2-1.37.0-win-64bit-build1.zip ... ok.
Extracting aria2-1.37.0-win-64bit-build1.zip ... done.
Linking ~\scoop\apps\aria2\current => ~\scoop\apps\aria2\1.37.0-1
Creating shim for 'aria2c'.
'aria2' (1.37.0-1) was installed successfully!
```
By default, Scoop displays a warning when running `scoop install` or `scoop update` with `aria2` enabled."
- the warning will be like this:
```powershell
WARN  Scoop uses 'aria2c' for multi-connection downloads.
WARN  Should it cause issues, run 'scoop config aria2-enabled false' to disable it.
WARN  To disable this warning, run 'scoop config aria2-warning-enabled false'.
```
#### install sudo
1. your input:
```powershell
scoop install sudo
```
2. the output
```powershell
WARN  Scoop uses 'aria2c' for multi-connection downloads.
WARN  Should it cause issues, run 'scoop config aria2-enabled false' to disable it.
WARN  To disable this warning, run 'scoop config aria2-warning-enabled false'.
Installing 'sudo' (0.2020.01.26) [64bit] from 'main' bucket
Starting download with aria2 ...
Download: Download Results:
Download: gid   |stat|avg speed  |path/URI
Download: ======+====+===========+=======================================================
Download: 18daca|OK  |   559KiB/s|C:/Users/zzy/scoop/cache/sudo#0.2020.01.26#7cd9a23.ps1
Download: Status Legend:
Download: (OK):download completed.
Checking hash of sudo.ps1 ... ok.
Linking ~\scoop\apps\sudo\current => ~\scoop\apps\sudo\0.2020.01.26
Creating shim for 'sudo'.
'sudo' (0.2020.01.26) was installed successfully!
```
## use `scoop list` to see what you've installed with Scoop

here you can also see the version, source, undated of these installed apps. 
```powershell
Installed apps:

Name  Version      Source Updated             Info
----  -------      ------ -------             ----
aria2 1.37.0-1     main   2025-01-04 14:25:30
sudo  0.2020.01.26 main   2025-01-04 14:42:51
```

## `scoop search` to check whether a package is available in Scoop
-  if you search for something , the output will be like this:
(i take curl as a example)
```powershell
Results from local buckets...
- 
Name    Version      Source Binaries
----    -------      ------ --------
gsudo   2.5.1        main
psutils 0.2023.06.28 main   sudo.ps1
sudo    0.2020.01.26 main
```
## updating Scoop
- This will download the latest version of scoop and update the local app manifests.
```powershell
scoop update
```
- If you want to update all your installed apps, you can run
```powershell
scoop update *
```
## add a new bucket
Sometimes, the program you want isn't in the default bucket. You can add another bucket:
```powershell
scoop bucket add BUCKET_NAME
```
# Bucket
In Scoop, a **bucket** is essentially a **repository of software packages**. The term comes from the idea of a container where software is stored, much like how you would have different containers for different types of items. In the context of Scoop, buckets help organize and categorize different types of software.

Here’s why buckets are useful:
- **Modularity**: Buckets allow you to manage software more efficiently. Instead of having all the software in one massive collection, you can add specific buckets that are relevant to your needs (e.g., development tools, multimedia software, etc.). For example, if you want to install programming-related tools, you might add the `main` and `extras` buckets.
- **Separation of Concerns**: Buckets help separate different categories of software. The `main` bucket contains stable, widely-used applications, while other buckets like `java` or `extras` provide niche or experimental software.
- **Extensibility**: You can add new buckets to expand Scoop’s functionality. For example, if you want to install software that's not in the default bucket, you can easily add another bucket.

For example:

- **Main Bucket**: Contains widely used, stable software like Git, Node.js, Python, etc.
- **Extras Bucket**: Contains additional software, including tools that might not be as commonly used but are still important for specific tasks (e.g., `7zip`, `vlc`).