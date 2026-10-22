- Linux stands as a fundamental pillar in cybersecurity, renowned for its robustness, flexibility, and open-source nature.
-  Linux is an operating system, just like Windows, macOS, iOS, or Android.
-  An operating system (OS) is software that manages all the hardware resources of a computer, facilitating communication between software applications and hardware components.
-  Unlike some other operating systems, Linux comes in many different distributions—often called "distros"—which are versions of Linux tailored to various needs and preferences.
-  Linux is generally considered more secure than other operating systems, and while it has had many kernel vulnerabilities in the past, it is becoming less and less frequent.
-  The overall Android operating system that runs on smartphones and tablets is based on the Linux kernel, and because of this, Linux is the most widely installed operating system.
-  An OS is software that manages all of the hardware resources associated with our computer.
-  Everything is a file	All system resources including hardware devices, processes, and network connections are represented as files, allowing them to be read from and written to using the same standard tools and commands.
- Small, single-purpose programs	Linux offers many different tools that we will work with, which can be combined to work together.
- Ability to chain programs together to perform complex tasks	The integration and combination of different tools enable us to carry out many large and complex tasks, such as processing or filtering specific data results.
- Avoid captive user interfaces	Linux is designed to work mainly with the shell (or terminal), which gives the user greater control over the operating system.
Configuration data stored in a text file	An example of such a file is the /etc/passwd file, which stores all users registered on the system.



## 1. Linux Filesystem Structure

Linux organises files and directories under a single root directory: `/`.

| Directory | Purpose | Cybersecurity relevance |
|---|---|---|
| `/` | Root of the entire filesystem | Starting point for absolute paths |
| `/home` | Regular users' home directories | User files and personal configurations |
| `/root` | Home directory of the root user | May contain administrator-specific files |
| `/etc` | System-wide configuration files | Investigating system configurations |
| `/var` | Variable data, including logs and caches | `/var/log` is important during investigations |
| `/tmp` | Temporary files | Unexpected files may warrant investigation |
| `/usr` | Applications, libraries, and shared resources | Common location for installed programs |
| `/bin` | Essential user commands; often linked to `/usr/bin` on modern systems | Contains commonly used commands |
| `/sbin` | System administration commands; often linked to `/usr/sbin` | Contains system utilities |
| `/dev` | Device files | Represents devices such as disks and terminals |
| `/proc` | Virtual filesystem exposing process and kernel information | Inspecting running processes and system state |
| `/sys` | Kernel and device information | Understanding hardware and kernel interfaces |
| `/boot` | Bootloader files and Linux kernels | Files relevant to system startup |
| `/mnt` | Common temporary mount point | Inspecting mounted filesystems |
| `/media` | Common mount point for removable media | USB drives and other removable devices |
| `/opt` | Often used for optional or third-party software | Locating additional installed applications |

**Remember:**
- `/` is the filesystem root; `/root` is the root user's home directory.
- `/etc` contains configuration files, while `/var/log` commonly contains logs.
- Hidden files and directories usually begin with a dot (`.`).
- Directory layouts can vary between Linux distributions.

### Absolute vs. relative paths

- **Absolute path:** Starts from `/`. Example: `/home/user/notes.txt`
- **Relative path:** Starts from your current working directory. Example: `notes.txt`
- `.` — current directory.
- `..` — parent directory.
- `~` — current user's home directory.

```bash
pwd
cd /var/log
cd ..
cd ~
```

---

## 2. Linux Navigation Commands

| Command | Purpose | Example |
|---|---|---|
| `pwd` | Display current working directory | `pwd` |
| `ls` | List directory contents | `ls` |
| `ls -l` | Detailed listing | `ls -l` |
| `ls -a` | Include hidden entries | `ls -a` |
| `ls -la` | Detailed listing including hidden entries | `ls -la` |
| `ls -lh` | Show sizes in human-readable format | `ls -lh` |
| `cd DIR` | Change directory | `cd /etc` |
| `cd ..` | Move to parent directory | `cd ..` |
| `cd ~` | Move to home directory | `cd ~` |
| `cd -` | Return to previous directory | `cd -` |

### Example

```bash
pwd
ls -la
cd /etc
pwd
cd ..
cd -
```

**Security relevance:** Navigation helps you locate configuration files, user directories, programs, and logs during system investigations.

---

## 3. File and Directory Management

| Command | Purpose | Example |
|---|---|---|
| `mkdir DIR` | Create a directory | `mkdir practice` |
| `mkdir -p a/b/c` | Create nested directories | `mkdir -p practice/logs/day1` |
| `touch FILE` | Create an empty file if absent; otherwise update timestamps | `touch notes.txt` |
| `cp SRC DEST` | Copy a file | `cp notes.txt backup.txt` |
| `cp -r SRC DEST` | Copy a directory recursively | `cp -r practice practice-backup` |
| `mv SRC DEST` | Move or rename a file/directory | `mv old.txt new.txt` |
| `rm FILE` | Delete a file | `rm old.txt` |
| `rmdir DIR` | Remove an empty directory | `rmdir emptydir` |
| `rm -r DIR` | Delete a directory and its contents recursively | `rm -r practice-backup` |

### Safe practice

```bash
mkdir -p ~/linux-practice/day11
cd ~/linux-practice/day11

touch sample.txt
cp sample.txt copy.txt
mv copy.txt renamed.txt
ls -l
rm renamed.txt
```

**Important:** `rm` usually does not move files to a recycle bin. Be particularly careful with `rm -r`, wildcards (`*`), and commands run with `sudo`. Practise inside a test directory.

---

## 4. Reading and Inspecting Files

| Command | Purpose | Example |
|---|---|---|
| `cat FILE` | Display file contents | `cat /etc/hostname` |
| `less FILE` | Browse a file page by page | `less /var/log/dpkg.log` |
| `head FILE` | Display first 10 lines by default | `head file.txt` |
| `head -n 20 FILE` | Display first 20 lines | `head -n 20 file.txt` |
| `tail FILE` | Display last 10 lines by default | `tail file.txt` |
| `tail -n 50 FILE` | Display last 50 lines | `tail -n 50 file.txt` |
| `tail -f FILE` | Follow new lines as a file grows | `tail -f application.log` |
| `file FILE` | Identify a file's type | `file unknown-file` |
| `stat FILE` | Display file metadata and timestamps | `stat notes.txt` |

### Useful `less` shortcuts

| Key | Action |
|---|---|
| `Space` | Move forward one page |
| `b` | Move backward one page |
| `/word` | Search for a word |
| `n` | Move to the next search match |
| `q` | Quit |

### Example

```bash
cat /etc/hostname
head -n 10 /etc/passwd
less /etc/os-release
```

**When to use what?**
- `cat`: Small files.
- `less`: Large files and logs.
- `head`: Inspect the beginning of a file.
- `tail`: Inspect the latest entries in a file.
- `tail -f`: Monitor new entries as they appear.

**Security relevance:** Analysts inspect files and logs to understand system state. Inspect unfamiliar files rather than executing them.

---

## 5. Getting Help in Linux

| Command | Purpose | Example |
|---|---|---|
| `man COMMAND` | Open a command's manual | `man ls` |
| `COMMAND --help` | Display brief usage information, when supported | `ls --help` |
| `whatis COMMAND` | Display a one-line description, if available | `whatis grep` |
| `apropos KEYWORD` | Search manual-page descriptions | `apropos directory` |
| `type COMMAND` | Explain how the shell resolves a command | `type cd` |
| `which COMMAND` | Locate an executable in the command path | `which python3` |

### Reading a manual page

```bash
man ls
```

Common sections:
- **NAME:** Command name and summary.
- **SYNOPSIS:** How to use the command.
- **DESCRIPTION:** What the command does.
- **OPTIONS:** Available flags and their meanings.

Inside `man`:
- `/word` — search.
- `n` — next match.
- `q` — exit.

**Note:** `cd` is normally a shell built-in, so its help may be available through `help cd` or `man bash` rather than a separate executable manual.

---

## 6. Wildcards and Quoting

Wildcards help match filenames. They are useful for navigation and file management.

| Pattern | Meaning | Example |
|---|---|---|
| `*` | Matches zero or more characters | `ls *.txt` |
| `?` | Matches one character | `ls file?.txt` |
| `[abc]` | Matches one character from the set | `ls report[12].txt` |

### Quotes

```bash
echo '$HOME'
echo "$HOME"
```

- Single quotes preserve the literal text `$HOME`.
- Double quotes allow `$HOME` to expand to the home directory path.

**Important:** Shell wildcards are not the same as regular expressions. More advanced text searching belongs to Day 12.

---

## 7. Basic System Identification

These commands help identify the machine and current user.

| Command | Purpose |
|---|---|
| `whoami` | Display the current effective username |
| `id` | Display user ID and group membership |
| `hostname` | Display the system hostname |
| `uname -a` | Display kernel and system information |
| `cat /etc/os-release` | Identify the Linux distribution |

Example:

```bash
whoami
id
hostname
uname -a
cat /etc/os-release
```

These are useful for confirming which machine and account you are working with during a lab.

---

## 8. Cybersecurity Relevance

Linux basics help security analysts:

1. **Navigate evidence:** Find configuration files, user directories, and logs.
2. **Inspect files:** Check file types, contents, ownership-related metadata, and timestamps.
3. **Understand system structure:** Know where programs, configurations, and logs commonly reside.
4. **Work safely:** Prefer read-only inspection before changing system state.
5. **Investigate efficiently:** Use `less`, `head`, and `tail` to inspect relevant portions of large files.

**Remember:** A hidden file, an unfamiliar file in `/tmp`, or an unusual filename is not automatically malicious. Investigate the context before reaching a conclusion.

---

## 9. Quick Revision — Commands to Remember

```bash
# Navigation
pwd
ls -la
cd /etc
cd ..
cd ~

# File and directory management
mkdir -p ~/linux-practice
touch sample.txt
cp sample.txt copy.txt
mv copy.txt renamed.txt
rm renamed.txt

# Inspect contents and metadata
cat /etc/hostname
less /etc/os-release
head -n 10 /etc/passwd
tail -n 20 somefile.log
file somefile
stat somefile

# Help
man ls
ls --help
help cd

# System identification
whoami
id
hostname
uname -a
cat /etc/os-release
```

Replace example filenames with paths that exist in your environment.

---

