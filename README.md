# Windows Command Prompt (CMD) Commands Guide

## Introduction

Welcome! This guide collects commonly used (and some advanced) native Windows Command Prompt (cmd.exe) commands to help with file management, networking, diagnostics, automation, and system administration.

Focus: Classic CMD commands (not full PowerShell coverage). Where a command is deprecated or superseded, a note is included. Many commands require an elevated (Administrator) prompt.

## How to Read & Use This Guide

Tips:
- Use `command /?` for built‑in help (often includes switches not listed here).
- Prefix with `runas /user:Administrator` or open an elevated terminal when access is denied.
- Combine commands with `&&` (only run next if success) or `||` (run next if failure).
- Use quotes around paths containing spaces: `"C:\Program Files\App"`.

Legend:
- (Admin) means the command typically needs elevation.
- (Deprecated) indicates the command is legacy; prefer the noted alternative.

## Table of Contents

1. File & Directory Management
2. Text, Search & Comparison
3. Permissions, Security & Ownership
4. Disk, Volume & Filesystem Tools
5. Networking & Connectivity
6. System Information & Diagnostics
7. Services, Processes & Scheduling
8. Boot, Recovery & Integrity
9. User & Account Management
10. Environment & Session Utilities
11. Scripting & Flow Control (Batch)
12. Miscellaneous & Console UX
13. Quick Task Examples

---
## 1. File & Directory Management

- `dir` – List directory contents (switches: `/a`, `/s`, `/b`, `/o`)
- `cd` / `chdir` – Change or show current directory
- `md` / `mkdir` – Create directory(ies)
- `rd` / `rmdir` – Remove directory (use `/s /q` for recursive quiet)
- `copy` – Copy files (simple)
- `xcopy` – Extended copy (legacy; prefer `robocopy` for reliability)
- `robocopy` – Robust Copy (retry logic, mirroring, multithread via `/MT`)
- `move` – Move/rename file(s)
- `ren` / `rename` – Rename file or directory
- `del` / `erase` – Delete file(s) (`/f /s /q` options)
- `forfiles` – Select files by date/age/mask for actions
- `type` – Display file contents
- `more` – Paginate output (`command | more`)
- `cls` – Clear screen
- `tree` – Visual directory tree
- `fsutil` (Admin) – Low‑level filesystem info (use cautiously)
- `subst` – Map a path to a virtual drive letter
- `pushd` / `popd` – Temporarily switch (and restore) directories
- `attrib` – View/change file attributes (+R +H +S +A)
- `where` – Locate executable(s) in PATH
- `comp` – Byte compare (basic)
- `fc` – File compare (text/binary diff)
- `copy con file.txt` – Quick inline file creation (Ctrl+Z to end)

## 2. Text, Search & Comparison

- `find` – Search for a string in a file (basic)
- `findstr` – Advanced text search with regex-like syntax
- `sort` – Sort input or a file
- `more` – Paginate output (listed above)
- `fc` – Compare files (relisted for context)
- `type` – Output file content (relisted)

## 3. Permissions, Security & Ownership

- `icacls` – View/modify NTFS ACLs (replaces legacy `cacls` / `xcacls`)
- `takeown` (Admin) – Take ownership of files/folders
- `cipher` – Encrypt/Decrypt (EFS) + wipe free space (`/w`)
- `whoami /groups` – Show group memberships
- `runas` – Run a program as another user
- `openfiles /query` (Admin) – List open network files

## 4. Disk, Volume & Filesystem Tools

- `chkdsk` (Admin) – Check disk for errors
- `diskpart` (Admin) – Disk partition manager (dangerous if misused)
- `format` (Admin) – Format volumes
- `label` – Change volume label
- `mountvol` – Manage volume mount points
- `vol` – Display volume label & serial
- `defrag` – Defragment drives
- `fsutil` (Admin) – (Also in section 1) advanced operations
- `cleanmgr` – Disk Cleanup utility launcher
- `compact` – Compress/uncompress NTFS files
- `sfc /scannow` (Admin) – System File Checker
- `dism /online /cleanup-image /restorehealth` (Admin) – Repair component store

## 5. Networking & Connectivity

- `ipconfig` – Adapter configuration (`/all`, `/release`, `/renew`, `/flushdns`)
- `ping` – Echo test
- `tracert` – Route path to destination
- `pathping` – Trace + packet loss statistics
- `arp -a` – ARP cache
- `nbtstat` – NetBIOS over TCP/IP diagnostics
- `netstat` – Active connections (`-a -n -o` common flags)
- `nslookup` – DNS queries (interactive mode available)
- `route print` – Routing table
- `route add|delete` – Edit routes
- `getmac` – Display MAC addresses
- `hostname` – Show machine name
- `telnet` – (Optional feature) legacy remote console (Deprecated)
- `ftp` – (Deprecated for secure use; prefer SFTP) basic file transfer
- `net` – Umbrella command: `net use`, `net share`, `net view`, etc.
- `net use` – Map/unmap network drives
- `net view` – List network devices/shares
- `net share` – Manage shared folders
- `net session` – List or close sessions
- `net time` – Query time server (legacy)
- `netsh` – Network shell (`interface`, `wlan`, `firewall`, `advfirewall`)
- `netsh wlan show profiles` – Saved Wi‑Fi profiles
- `netdom` (Domain) – Domain trust & join operations
- `certutil -urlcache * delete` – Clear URL cache (diagnostics/security)

## 6. System Information & Diagnostics

- `systeminfo` – OS + hardware summary
- `ver` – Windows version
- `set` – Show environment variables
- `driverquery` – Installed drivers list
- `msinfo32` – System Information GUI
- `wmic` (Deprecated) – WMI queries (use PowerShell CIM/WMI cmdlets)
- `dxdiag` – DirectX diagnostics
- `tasklist` – Running processes
- `tasklist /svc` – Map services to processes
- `eventvwr` – Event Viewer (GUI)
- `wevtutil` (Admin) – Query/clear event logs
- `perfmon` – Performance Monitor GUI
- `powercfg /energy` (Admin) – Power diagnostics report
- `gpresult /r` – Group Policy resultant set
- `echo %ERRORLEVEL%` – Last command exit code

## 7. Services, Processes & Scheduling

- `taskkill /PID <id> /F` – Force terminate process
- `sc query` – Service status
- `sc start|stop|config` – Control services
- `services.msc` – Services GUI
- `schtasks /create` – Schedule tasks
- `schtasks /query /fo LIST /v` – View tasks verbose
- `timeout /t <seconds>` – Delay execution
- `start` – Launch a program/window (`start "Title" command`)

## 8. Boot, Recovery & Integrity

- `bcdedit` (Admin) – Boot configuration
- `bootrec` (Recovery Env) – Repair boot records
- `reagentc /info` – Windows Recovery Environment (WinRE) status
- `sfc /scannow` (Admin) – System file scan (listed earlier)
- `dism /online /cleanup-image /restorehealth` – Component store repair (listed earlier)

## 9. User & Account Management

- `net user` – List/create/modify local users
- `net localgroup` – Local group membership
- `net group` (Domain) – Domain group management
- `whoami` – Current user & SID info
- `whoami /priv` – Privileges list
- `runas /user:<User>` – Execute under another account
- `control userpasswords2` – Advanced user GUI
- `lusrmgr.msc` – Local Users & Groups (not in Home editions)

## 10. Environment & Session Utilities

- `set` – Display/set session environment variables
- `setx` – Persist environment variables (new sessions only)
- `path` – View/edit PATH (session)
- `title` – Set console window title
- `color` – Set console colors
- `mode con` – Console dimensions and buffer
- `echo` – Output text / toggle command echoing
- `pause` – Wait for user keystroke
- `call` – Invoke another batch file and return
- `exit` – Exit CMD / set errorlevel: `exit /b 1`

## 11. Scripting & Flow Control (Batch)

- `for` – Iterate (files, strings, numbers); `for /?` for forms
- `if` – Conditional execution (string, errorlevel, exist)
- `goto` – Jump to label
- `choice` – Prompt for user selection, sets `%ERRORLEVEL%`
- `shift` – Shift batch parameters `%1..%9`
- `set /a` – Arithmetic operations
- `rem` or `::` – Comments
- `>`, `>>` – Redirect (overwrite / append)
- `2>&1` – Merge stderr into stdout
- `|` – Pipe output to another command

## 12. Miscellaneous & Console UX

- `help` – Built-in help index
- `assoc` – File extension associations
- `ftype` – File type command mapping
- `time` – Show/set system time
- `date` – Show/set system date
- `shutdown /s /t 0` – Immediate shutdown
- `shutdown /r /t 0` – Immediate restart
- `shutdown /h` – Hibernate
- `shutdown /l` – Log off
- `shutdown /a` – Abort pending shutdown
- `msconfig` – System Configuration GUI
- `mmc` – Microsoft Management Console
- `taskmgr` – Task Manager
- `clip` – Redirect output to clipboard (e.g., `ipconfig | clip`)

## 13. Quick Task Examples

Create a directory tree and move files:
```
md logs\archived && move *.log logs\
```

Find lines containing ERROR (case-insensitive) in all `.txt` files:
```
findstr /i /n /s /c:"ERROR" *.txt
```

Mirror a directory to backup (with logging):
```
robocopy C:\Source D:\Backup /MIR /R:2 /W:2 /LOG:backup.log
```

Kill a hung process by name:
```
taskkill /IM notepad.exe /F
```

List top TCP listeners:
```
netstat -ano | findstr LISTENING
```

Set a persistent environment variable (new sessions only):
```
setx APP_ENV production
```

Generate a power efficiency report (HTML):
```
powercfg /energy /output energy-report.html
```

Flush DNS cache:
```
ipconfig /flushdns
```

## Deprecated / Legacy Notes

- `wmic` – Deprecated; prefer PowerShell CIM cmdlets.
- `telnet`, `ftp` – Insecure; use SSH/SFTP alternatives.
- `xcopy` – Superseded for most tasks by `robocopy`.
- `deltree` – Removed after Windows 9x era (use `rd /s`).
- `xcacls` / `cacls` – Deprecated; use `icacls`.

## Safety Disclaimer
Commands like `diskpart`, `format`, `bcdedit`, `bootrec`, `dism`, and `sfc` can cause system instability or data loss if misused. Always verify targets and consider backing up important data.

---
### Contribution
We welcome contributions! If you'd like to contribute to this project, please check out our [Contribution Guidelines](Contribution.md).

### Code of Conduct
Please review our [Code of Conduct](CodeOfConduct.md) before participating in this project.

## License
This project is licensed under the [License](LICENSE).