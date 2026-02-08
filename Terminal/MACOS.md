# macOS Terminal Commands (bash / zsh)

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

## System Information

- `top` → Show running processes
- `ps aux` → List all processes
- `kill <PID>` → Kill process by PID
- `killall <process_name>` → Kill process by name
- `df -h` → Disk usage
- `du -sh <folder>` → Size of folder
- `uptime` → System uptime
- `whoami` → Current user
- `hostname` → Hostname of machine

## Networking

- `ifconfig` → Network interfaces
- `ping <host>` → Ping host
- `traceroute <host>` → Trace route
- `netstat -an` → Network connections
- `curl <url>` → HTTP request

## Environment Variables

- `echo $PATH` → Show PATH
- `export VAR_NAME=value` → Set environment variable (temporary)
- `echo $VAR_NAME` → Show variable
- Add to `~/.zshrc` or `~/.bash_profile` for persistent export

## Package Management

- `brew install <package>` → Install package via Homebrew
- `brew update` → Update Homebrew
- `brew upgrade` → Upgrade installed packages
- `brew list` → List installed packages
- `brew search <package>` → Search package

## Shortcuts / Productivity

- `Tab` → Auto-complete file/folder names
- `Ctrl + A` → Move cursor to beginning of line
- `Ctrl + E` → Move cursor to end of line
- `Ctrl + U` → Delete to beginning of line
- `Ctrl + K` → Delete to end of line
- `Ctrl + R` → Reverse search command history
- `!!` → Run last command
