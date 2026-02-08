# Windows Terminal Commands (CMD & PowerShell)

## File & Folder Navigation

- `cd <folder>` → Change directory
- `cd ..` → Go up one folder
- `dir` → List directory contents
- `dir /a` → List all files including hidden
- `mkdir <folder>` → Create a folder
- `rmdir /s /q <folder>` → Delete folder and contents
- `del <file>` → Delete a file
- `copy <source> <destination>` → Copy file
- `move <source> <destination>` → Move file

## System Information

- `systeminfo` → View system info
- `tasklist` → List running processes
- `taskkill /PID <pid> /F` → Kill process by PID
- `ipconfig` → Network configuration
- `ipconfig /all` → Detailed network info
- `ping <host>` → Check connectivity
- `tracert <host>` → Trace route to host
- `netstat -ano` → Show network connections & ports

## PowerShell Basics

- `Get-Process` → List processes
- `Stop-Process -Id <PID>` → Kill process by PID
- `Get-Service` → List services
- `Start-Service <service>` → Start service
- `Stop-Service <service>` → Stop service
- `Get-Command` → List all PowerShell commands
- `Get-Help <command>` → Get help for a command

## Environment & Variables

- `set` → Show all environment variables
- `setx <name> <value>` → Set persistent environment variable
- `%PATH%` → View current PATH
- `$env:PATH` → PowerShell view PATH

## Package Management (Optional)

- `winget search <package>` → Search packages
- `winget install <package>` → Install package
- `choco install <package>` → Install via Chocolatey
- `choco upgrade all` → Upgrade all packages

## Useful Shortcuts

- `Ctrl + C` → Stop running command
- `Tab` → Auto-complete file/folder names
- `F7` → Command history in CMD
- `Alt + F7` → Clear command history in CMD
