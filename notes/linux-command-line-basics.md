# Linux Command Line Basics

Beginner-friendly Linux terminal notes with clear command explanations and examples.

---

## What is Linux?

- **Operating System (OS)** examples: Windows, macOS, Linux.
- **Linux kernel**: the core part of the OS.
- It connects software (applications) to hardware (CPU, RAM, disk, devices).

## Terminal & Shell

- **Terminal**: the program/window where you type commands.
- **Shell**: the command interpreter (user interface) that interacts with the OS.
- Common shells: `bash`, `zsh`
- Prompt symbols:
    - `$` normal user
    - `#` root (administrator)

---

## Basic Commands (Essentials)

### Where am I?

- `pwd` — print working directory (shows your current location)

### List files and folders

- `ls` — list directory contents
    - `ls -a` show hidden files
    - `ls -l` long format
    - `ls -la` hidden + long format

### Move between directories

- `cd <dir>` — change directory
    - `cd Desktop`
    - `cd ..` go up one directory
    - `cd -` go back to the previous directory
    - `cd ~` go to home directory
    - `cd /` go to root directory

### Clear the terminal

- `clear` — clears the terminal screen

### Who am I?

- `whoami` — shows the current user

### View file content

- `cat file.txt` — print file content
- `more file.txt` / `less file.txt` — view long files page by page

---

## Identity, Users, and Groups

### User / group IDs

- `id` — shows UID, primary group (GID), and secondary groups

### Hostname

- `hostname` — machine name on the network

### User management (admin)

> Requires admin/root permissions (`sudo`).
> 
- `sudo <command>` — run command with administrator rights
- `adduser <name>` — create a new user (Debian/Ubuntu)
- `userdel <name>` — delete a user
- `passwd` — change password
- `chsh` — change login shell
- `cat /etc/passwd` — list users (system + normal)
- `cat /etc/shadow` — password hashes (root only)

---

## Files & Directories (Create / Copy / Move / Delete)

### Create

- `touch file.txt` — create an empty file
- `mkdir folder` — create a directory

### Copy

- `cp src dst` — copy file (e.g. `cp file1.txt backup.txt`)
- `cp -r dir1 dir2` — copy directory recursively

### Move / rename

- `mv src dst` — move or rename (e.g. `mv old.txt new.txt`)

### Remove (be careful)

- `rm file.txt` — remove file
- `rmdir folder` — remove empty directory
- `rm -r folder` — remove directory (recursive)
- `rm -rf folder` — force remove ⚠️ dangerous

---

## Find help

- `man <command>` — manual page (e.g. `man ls`)
- `apropos <keyword>` — search for commands by keyword
- `which <command>` — shows the path of a command (e.g. `which python`)

---

## Linux Directories (Very Important)

- `/home` — users' home directories
- `/root` — root user home directory
- `/bin` — essential user commands (binaries)
- `/sbin` — system/admin commands
- `/etc` — system configuration files
- `/var` — variable data (logs, cache, spool)
- `/tmp` — temporary files
- `/dev` — devices (disks, terminals, etc.)

---

## Storage

- `lsblk` — list disks and partitions

## Mounting

- `mount` — show mounted filesystems
- `mount <device> <mount_point>` — manual mounting (admin)

---

## Networking (basics)

- `ifconfig` (legacy) / `ip a` (modern) — network interfaces and IP addresses
- `netstat` (legacy) / `ss` (modern) — connections and listening ports

### Network Interface Details (from `ifconfig`)

- **MAC address** — unique hardware address of the network card (e.g. `08:00:27:da:bb:d9`)
- **Netmask** — defines the size of the local network (e.g. `255.255.255.0` → up to 254 usable host IPs)
- **Broadcast address** — send to all devices on the same network (e.g. `10.0.2.255`)
- **RX / TX** — received (RX) and transmitted (TX) data totals

---

## Processes & System Monitoring

### List processes

- `ps aux` — list running processes
- `top` — live process view (CPU/RAM)

### Kill a process

- `kill <PID>` — stop a process (sends `SIGTERM`)
- `kill -9 <PID>` — force stop (`SIGKILL`)
- `pkill <name>` — kill a process by name
- `kill -l` — list available signals

### Find a PID

- `ps aux | grep <name>`
- `pgrep <name>` (if available)

---

## Job Control

- `Ctrl+Z` — suspend (pause) the currently running process
- `jobs` — list suspended/background jobs
- `fg %1` — bring job 1 back to the foreground
- `bg %1` — resume job 1 in the background
- `Ctrl+C` — interrupt/kill the currently running process
- `pstree` — display running processes as a tree (parent → children)

> Tip: job control (`jobs`, `fg`, `bg`) is for processes started in *your current terminal session*.
> 

---

## systemd (Services / Daemons)

A **daemon** is a background program that runs without a visible interface. `systemd` is the main service manager on many Linux distros.

- `systemctl status <service>`
- `systemctl start <service>`
- `systemctl stop <service>`
- `systemctl enable <service>` — start at boot
- `systemctl disable <service>`
- `systemctl list-units`

**Unit types:**

- `service` — background service
- `socket` — socket activation
- `timer` — scheduled unit
- `target` — grouping unit (boot goals)

---

## SSH (Remote Access)

- `ssh user@host` — connect (e.g. `ssh ayoub@192.168.1.100`)
- `ssh -p 2222 user@host` — custom port
- `ssh -i ~/.ssh/key.pem user@host` — use a private key

---

## Package Managers

### apt (Debian/Ubuntu)

- `sudo apt update` — refresh package lists
- `sudo apt install <package>`
- `sudo apt remove <package>`
- `sudo apt upgrade` — upgrade installed packages

### snap

- `snap find <app>`
- `sudo snap install <app>`
- `snap list`

---

## Terminal Shortcuts

- `Ctrl+U` — delete everything before the cursor
- `Ctrl+K` — delete everything after the cursor
- `Ctrl+Y` — paste back what was just deleted
- `Ctrl+A` — jump to beginning of the line
- `Ctrl+E` — jump to end of the line

### Aliases

- `alias name="command"` — create a shortcut for a longer command
- Make it permanent by adding it to `~/.bashrc` (or `~/.zshrc`) then run `source ~/.bashrc`

---

## Understanding the Prompt

- `$` — normal user
- `#` — root (administrator)

> If you see `#`, commands run with full admin privileges (no `sudo` needed) — mistakes can be much more dangerous.
> 

# **Done By AYOUB BOUAYAD**
