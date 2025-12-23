# Linux Fundamentals for DevOps (Practical & No-Fluff)

This document covers the **core Linux concepts every DevOps engineer must master**.
It focuses on **real-world usage**, not academic theory.

---

## 1. What is Linux (DevOps Context)

Linux is an **open-source operating system** used by the majority of servers in production.
As a DevOps engineer, you will:
- Deploy applications on Linux servers
- Debug issues via the command line
- Manage permissions, services, logs, and processes

If you are not comfortable with Linux CLI, **you cannot survive in DevOps**.

---

## 2. Basic Linux Commands (Must Be Muscle Memory)

### `ls` – List files
```bash
ls
ls -l
ls -la
```

- `-l` → long format (permissions, owner, size)
- `-a` → include hidden files (`.env`, `.ssh`)

---

### `cp` – Copy files
```bash
cp file.txt backup.txt
cp -r config/ config_backup/
```

---

### `mv` – Move / rename files
```bash
mv app.conf app.conf.bak
mv old_dir/ new_dir/
```

---

### `rm` – Delete files (dangerous)
```bash
rm file.txt
rm -r logs/
rm -rf logs/
```

⚠️ `rm -rf` has **no undo**.

---

## 3. Linux File System Hierarchy (CRITICAL)

```
/        → root of the filesystem
/home    → user home directories
/etc     → configuration files
/var     → logs & variable data
/usr     → installed programs
/tmp     → temporary files
```

---

## 4. Permissions & Ownership (MOST IMPORTANT)

### Reading permissions
```bash
ls -l
```

Example:
```
-rwxr-xr-- 1 root docker 512 app.sh
```

---

## 5. `chmod` – Change Permissions

```bash
chmod 755 app.sh
chmod +x script.sh
```

---

## 6. `chown` – Change Ownership (DEEP EXPLANATION)

### Syntax
```bash
chown USER:GROUP file
```

### Example
```bash
sudo chown -R www-data:www-data /var/www/html
```

---

## 7. Processes & Signals

```bash
ps aux | grep ssh
top
kill PID
```

---

## 8. Package Management (Ubuntu)

```bash
sudo apt update
sudo apt install nginx
```

---

## 9. Bash Basics

```bash
NAME="Adarsh"
echo $NAME
```

---

## 10. SSH (Secure Shell) – CRITICAL FOR DEVOPS

SSH allows you to **connect securely to remote Linux servers**.
Almost all DevOps work happens over SSH.

### Basic SSH login
```bash
ssh username@server_ip
```

Example:
```bash
ssh chadarsh98@192.168.64.3
```

---

### SSH with custom port
```bash
ssh -p 2222 username@server_ip
```

---

### SSH using key-based authentication
```bash
ssh -i ~/.ssh/id_rsa username@server_ip
```

Key-based SSH is **mandatory in production** (passwords are insecure).

---

### Check SSH service
```bash
systemctl status ssh
```

Logs:
```bash
journalctl -u ssh
```

---

## 11. SCP (Secure Copy) – File Transfer Over SSH

SCP is used to **copy files between local and remote systems securely**.

### Copy local file → remote server
```bash
scp file.txt username@server_ip:/home/username/
```

---

### Copy remote file → local system
```bash
scp username@server_ip:/home/username/file.txt ./
```

---

### Copy directories recursively
```bash
scp -r project/ username@server_ip:/opt/project/
```

---

### SCP with custom port
```bash
scp -P 2222 file.txt username@server_ip:/home/username/
```

---

## 12. Practice Tasks (DO THESE)

1. SSH into your Ubuntu VM from macOS
2. Copy a file from local → VM using `scp`
3. Change ownership of that file using `chown`
4. Modify permissions using `chmod`
5. Verify with `ls -l`

---

## Final Verdict

If you can:
- SSH into servers confidently
- Use SCP without Googling
- Fix permission issues
- Read logs when SSH fails

You are **ready for real DevOps workflows**.
