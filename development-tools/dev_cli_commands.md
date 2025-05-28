# 🖥️ Developer's CLI Command Guide

<div align="center">
  <i>A comprehensive reference for command-line tools used in daily development workflows</i>
</div>

---

## 🔍 Process Management

### View Processes
| Command | Description |
|---------|-------------|
| `ps aux` | List all running processes |
| `ps -ef` | Full format listing of all processes |
| `top` | Interactive process viewer (press 'q' to quit) |
| `htop` | Enhanced interactive process viewer with colors and graphs |
| `ps -ef \| grep "keyword"` | Find processes containing keyword |
| `ps -ef \| grep 3000` | Find processes using port 3000 |

### Process Control
| Command | Description |
|---------|-------------|
| `kill PID` | Terminate a process by its process ID |
| `kill -9 PID` | Force terminate a process |
| `killall processname` | Kill all processes with the given name |
| `pkill processname` | Similar to killall, sends signal to processes |
| `nohup command &` | Run command immune to hangups, output to nohup.out |
| `command &` | Run command in background |

---

## 📁 File Operations

### Navigation and Viewing
| Command | Description |
|---------|-------------|
| `ls -la` | List all files with details |
| `cd path/to/directory` | Change directory |
| `pwd` | Print working directory |
| `cat filename` | Display file content |
| `less filename` | View file content with pagination |
| `head -n 10 filename` | Show first 10 lines |
| `tail -n 10 filename` | Show last 10 lines |
| `tail -f logfile` | Follow file updates in real-time |

### File Management
| Command | Description |
|---------|-------------|
| `touch filename` | Create empty file or update timestamp |
| `mkdir directory` | Create directory |
| `mkdir -p path/to/nested/directory` | Create nested directories |
| `rm filename` | Remove file |
| `rm -r directory` | Remove directory and contents |
| `cp source destination` | Copy file |
| `cp -r source_dir destination_dir` | Copy directory recursively |
| `mv source destination` | Move or rename file/directory |
| `find . -name "pattern"` | Find files by name |
| `find . -type f -exec command {} \;` | Execute command on each file |

---

## 📝 Text Processing

### Search and Manipulation
| Command | Description |
|---------|-------------|
| `grep "pattern" filename` | Search for pattern in file |
| `grep -r "pattern" directory` | Recursive search |
| `grep -i "pattern" filename` | Case-insensitive search |
| `sed 's/find/replace/g' filename` | Find and replace text |
| `awk '{print $1}' filename` | Print first column |
| `sort filename` | Sort lines alphabetically |
| `uniq filename` | Remove duplicate lines (requires sorted input) |
| `sort filename \| uniq` | Sort and remove duplicates |
| `wc -l filename` | Count lines in file |

---

## 🌐 Network Tools

### Connectivity
| Command | Description |
|---------|-------------|
| `ping hostname` | Test connectivity to host |
| `curl URL` | Make HTTP request and show response |
| `wget URL` | Download file from URL |
| `ssh user@hostname` | Connect to remote server |
| `scp file user@hostname:/path` | Copy file to remote server |
| `rsync -avz source user@hostname:/path` | Sync files to remote location |

### Ports and Services
| Command | Description |
|---------|-------------|
| `netstat -tuln` | List listening ports |
| `lsof -i :portNumber` | List processes using the specified port |
| `ss -tuln` | Socket statistics (modern alternative to netstat) |
| `ifconfig` or `ip addr` | Show network interfaces |
| `dig domain` | DNS lookup |
| `nslookup domain` | Name server lookup |

---

## 📦 Package Management (Ubuntu/Debian)

| Command | Description |
|---------|-------------|
| `apt update` | Update package lists |
| `apt upgrade` | Upgrade installed packages |
| `apt install packagename` | Install package |
| `apt remove packagename` | Remove package |
| `dpkg -l` | List all installed packages |

---

## 🔄 Git Commands

| Command | Description |
|---------|-------------|
| `git init` | Initialize repository |
| `git clone URL` | Clone repository |
| `git status` | Show working tree status |
| `git add filename` | Stage changes |
| `git commit -m "message"` | Commit changes |
| `git push` | Push commits to remote |
| `git pull` | Pull changes from remote |
| `git branch` | List branches |
| `git checkout branchname` | Switch branches |
| `git log` | Show commit history |
| `git diff` | Show changes between commits |

---

## 💻 System Information

| Command | Description |
|---------|-------------|
| `df -h` | Disk usage |
| `du -sh directory` | Directory size |
| `free -h` | Memory usage |
| `uname -a` | System information |
| `lscpu` | CPU information |
| `uptime` | System uptime |
| `history` | Command history |

---

## 🗜️ File Compression

| Command | Description |
|---------|-------------|
| `tar -czvf archive.tar.gz directory/` | Create compressed archive |
| `tar -xzvf archive.tar.gz` | Extract compressed archive |
| `zip -r archive.zip directory/` | Create zip archive |
| `unzip archive.zip` | Extract zip archive |

---

## 🐳 Docker Commands

| Command | Description |
|---------|-------------|
| `docker ps` | List running containers |
| `docker images` | List images |
| `docker build -t name .` | Build image from Dockerfile |
| `docker run -p 8080:80 image` | Run container with port mapping |
| `docker-compose up` | Start services defined in docker-compose.yml |
| `docker exec -it container bash` | Open shell in running container |

---

## 🔧 Environment and Variables

| Command | Description |
|---------|-------------|
| `env` | Display environment variables |
| `echo $VARIABLE` | Display value of environment variable |
| `export VARIABLE=value` | Set environment variable |
| `alias name='command'` | Create command alias |

---

## 👤 User Management

| Command | Description |
|---------|-------------|
| `sudo command` | Execute command as superuser |
| `whoami` | Show current username |
| `passwd` | Change password |
| `chown user:group file` | Change file ownership |
| `chmod permissions file` | Change file permissions |

---

## ⏱️ Process Supervision and Background Jobs

| Command | Description |
|---------|-------------|
| `screen` | Terminal multiplexer (detach with Ctrl+A, D) |
| `tmux` | Modern terminal multiplexer |
| `jobs` | List background jobs |
| `fg` | Bring job to foreground |
| `bg` | Send job to background |
| `nohup command &` | Run command immune to hangups |
| `command & disown` | Run command in background and disown from shell |

---

## 🔒 Security and SSH

| Command | Description |
|---------|-------------|
| `ssh-keygen` | Generate SSH key pair |
| `ssh-copy-id user@hostname` | Copy SSH key to server |
| `openssl enc -aes-256-cbc -in file -out file.enc` | Encrypt file |
| `openssl enc -d -aes-256-cbc -in file.enc -out file` | Decrypt file |

---

## 💡 Tips for Efficient CLI Usage

| Technique | Description |
|-----------|-------------|
| `Tab` | Use for command completion |
| `Ctrl+R` | Press for reverse history search |
| `!!` | Use to repeat the last command |
| `command \| xargs command2` | Pass output as arguments |
| `>` or `>>` | Redirect output (overwrite) or (append) |
| `\|` | Pipe commands to chain operations |
| `&&` or `;` | Combine commands (run second if first succeeds) or (run regardless) |

<div align="center">
  <p><strong>Happy command-line coding!</strong></p>
</div> 