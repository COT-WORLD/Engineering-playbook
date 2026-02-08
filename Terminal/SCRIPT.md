# System Commands (Windows / macOS / Linux)

## 1. Processes & Services

### Windows

- `tasklist` → List running processes
- `taskkill /PID <pid> /F` → Kill process by PID
- `Get-Process` → List processes (PowerShell)
- `Stop-Process -Id <PID>` → Kill process (PowerShell)
- `Get-Service` → List services
- `Start-Service <service>` → Start service
- `Stop-Service <service>` → Stop service

### macOS / Linux

- `ps aux` → List all processes
- `top` → Interactive process monitor
- `htop` → Interactive process monitor (installable)
- `kill <PID>` → Kill process by PID
- `killall <process_name>` → Kill process by name
- `systemctl status <service>` → Check service (Linux)
- `sudo systemctl start <service>` → Start service (Linux)
- `sudo systemctl stop <service>` → Stop service (Linux)
- `brew services list` → List services (macOS)
- `brew services start <service>` → Start service (macOS)
- `brew services stop <service>` → Stop service (macOS)

---

## 2. Disk Usage & Storage

### Windows

- `dir` → List files and folders
- `chkdsk` → Check disk
- `wmic logicaldisk get size,freespace,caption` → Check free/total disk space
- `fsutil volume diskfree c:` → Check free space on C:

### macOS / Linux

- `df -h` → Disk usage by filesystem
- `du -sh <folder>` → Size of a folder
- `ls -lh` → Human-readable file sizes
- `diskutil list` → List disks (macOS)
- `df -H` → Disk usage in macOS style

---

## 3. Memory Usage

### Windows

- `systeminfo` → Displays total and available memory
- `wmic OS get FreePhysicalMemory,TotalVisibleMemorySize /Format:List` → Memory info
- `tasklist` → Shows memory used by processes

### macOS / Linux

- `free -h` → Memory usage
- `vm_stat` → Virtual memory statistics (macOS)
- `top` or `htop` → Interactive memory usage by process
- `cat /proc/meminfo` → Detailed memory info (Linux)

---

## 4. CPU Monitoring

### Windows

- `wmic cpu get loadpercentage` → CPU usage
- `typeperf "\Processor(_Total)\% Processor Time"` → Real-time CPU usage
- `taskmgr` → Open Task Manager GUI

### macOS / Linux

- `top` → CPU usage per process
- `htop` → Interactive CPU monitoring
- `mpstat` → CPU usage (Linux, install via `sysstat`)
- `sysctl -n machdep.cpu.brand_string` → CPU info (macOS)
- `lscpu` → CPU info (Linux)

---

## 5. Networking

### Windows

- `ipconfig` → Show IP addresses
- `ipconfig /all` → Detailed network info
- `ping <host>` → Test connectivity
- `tracert <host>` → Trace route
- `netstat -ano` → Network connections
- `nslookup <host>` → DNS lookup

### macOS / Linux

- `ifconfig` or `ip a` → Network interfaces
- `ping <host>` → Test connectivity
- `traceroute <host>` → Trace route
- `netstat -tuln` → Show open ports
- `dig <host>` → DNS lookup
- `curl <url>` → HTTP requests
- `wget <url>` → Download files

---

## 6. Quick Productivity Shortcuts (Terminal)

- `Ctrl + C` → Stop running command
- `Ctrl + Z` → Pause process and send to background
- `fg` → Bring background process to foreground
- `jobs` → List background processes
- `clear` → Clear terminal screen
