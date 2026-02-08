# Linux Terminal Commands (Ubuntu / Debian / Linux)

## File & Folder Navigation

- `pwd` → Show current directory
- `ls` → List files
- `ls -la` → List all files including hidden with details
- `cd <folder>` → Change directory
- `cd ..` → Go up one folder
- `mkdir <folder>` → Create new directory
- `rm <file>` → Delete file
- `rm -rf <folder>` → Delete folder recursively
- `cp <source> <destination>` → Copy file/folder
- `mv <source> <destination>` → Move file/folder

## File Viewing & Editing

- `cat <file>` → Display file contents
- `less <file>` → Scroll through file
- `head <file>` → First 10 lines
- `tail <file>` → Last 10 lines
- `nano <file>` → Edit file in terminal
- `vim <file>` → Edit file using Vim
- `touch <file>` → Create empty file

## System Information & Processes

- `top` → Show running processes
- `htop` → Interactive process viewer (install via `sudo apt install htop`)
- `ps aux` → List all processes
- `kill <PID>` → Kill process by PID
- `killall <process_name>` → Kill process by name
- `uptime` → System uptime
- `df -h` → Disk usage
- `du -sh <folder>` → Size of folder
- `free -h` → Memory usage
- `whoami` → Current user
- `hostname` → Hostname of machine

## Networking

- `ifconfig` or `ip a` → Show network interfaces
- `ping <host>` → Ping host
- `traceroute <host>` → Trace route
- `netstat -tuln` → Show listening ports
- `curl <url>` → HTTP request
- `wget <url>` → Download file

## Package Management

### Debian/Ubuntu

- `sudo apt update` → Update package list
- `sudo apt upgrade` → Upgrade installed packages
- `sudo apt install <package>` → Install package
- `sudo apt remove <package>` → Remove package
- `dpkg -l` → List installed packages

### RedHat/CentOS

- `sudo yum install <package>` → Install package
- `sudo yum update` → Update packages

### Arch Linux

- `sudo pacman -S <package>` → Install package
- `sudo pacman -Syu` → Update system

## Environment Variables

- `echo $PATH` → Show PATH
- `export VAR_NAME=value` → Set temporary environment variable
- `echo $VAR_NAME` → Show variable
- Add to `~/.bashrc` or `~/.zshrc` for persistent variables

## Shortcuts / Productivity

- `Tab` → Auto-complete file/folder names
- `Ctrl + A` → Move cursor to beginning of line
- `Ctrl + E` → Move cursor to end of line
- `Ctrl + U` → Delete to beginning of line
- `Ctrl + K` → Delete to end of line
- `Ctrl + R` → Reverse search command history
- `!!` → Run last command
- `!n` → Run nth command from history
- `history` → Show command history
