
# 🔍 Search & Filter in Linux 

---

## 1️⃣ Introduction to Search & Filter

In Linux, systems generate **thousands of files and log lines**.

Searching means:

- Finding files
- Finding text inside files

Filtering means:

- Selecting only useful lines
- Removing unwanted data

Think like this:

- Google search = `find`
- Filtering results = `grep`, `sort`, `uniq`

---

## 2️⃣ Why Searching is Important in Linux

In real systems, you must:

- Find log errors quickly
- Locate large files
- Search configuration entries
- Troubleshoot issues fast

Example:

```bash
# Find "error" in a log file
grep error /var/log/syslog
```

---

## 3️⃣ Reading Files with cat

`cat` means **concatenate** but mostly used to read files.

Example:

```bash
cat file.txt
```

Read line numbers:

```bash
cat -n file.txt
```

Combine multiple files:

```bash
cat file1 file2
```

---

## 4️⃣ Filtering Text with grep

`grep` searches **text inside files**.

Basic search:

```bash
grep root /etc/passwd
```

Case-insensitive search:

```bash
grep -i error logfile.txt
```

Show line numbers:

```bash
grep -n ssh /var/log/auth.log
```

Count matches:

```bash
grep -c failed logfile.txt
```

---

## 5️⃣ Using Pipes for Filtering

Pipe (`|`) sends output of one command to another.

Example:

```bash
cat /etc/passwd | grep bash
```

This means:

- Read file
- Filter only lines with bash

---

## 6️⃣ Sorting Data with sort

Sort lines alphabetically:

```bash
sort names.txt
```

Sort in reverse:

```bash
sort -r names.txt
```

Sort numerically:

```bash
sort -n numbers.txt
```

---

## 7️⃣ Removing Duplicates with uniq

`uniq` removes duplicate lines (must be sorted first).

Example:

```bash
sort data.txt | uniq
```

Count duplicates:

```bash
sort data.txt | uniq -c
```

---

## 8️⃣ Introduction to find Command

`find` searches **files and directories** in filesystem.

Basic syntax:

```bash
find <path> <options> <action>
```

Example:

```bash
find /home -name file.txt
```

---

## 9️⃣ Finding Files by Name

Find by exact name:

```bash
find / -name passwd
```

Case-insensitive:

```bash
find / -iname "*.log"
```

---

## 🔟 Finding Files by Type

Find only files:

```bash
find /var -type f
```

Find only directories:

```bash
find /etc -type d
```

---

## 1️⃣1️⃣ Finding Files by Size

Find files larger than 100MB:

```bash
find / -size +100M
```

Find files smaller than 10KB:

```bash
find / -size -10k
```

---

## 1️⃣2️⃣ Finding Files by Date

Modified in last 1 day:

```bash
find /home -mtime -1
```

Modified more than 30 days ago:

```bash
find /var/log -mtime +30
```

---

## 1️⃣3️⃣ Advanced find Options

Delete found files:

```bash
find /tmp -type f -mtime +7 -delete
```

Execute command on found files:

```bash
find /var/log -name "*.log" -exec rm {} \;
```

---

## 1️⃣4️⃣ Real-Time Use Cases

1. Find error in logs:

```bash
grep error /var/log/syslog
```

2. Find big files:

```bash
find / -size +1G
```

3. Delete old logs:

```bash
find /var/log -name "*.log" -mtime +30 -delete
```

---

## 🧪 1️⃣5️⃣ Hands-on Labs

### Lab 1: grep Practice

1. Create file with few lines
2. Search a word using grep
3. Use -i and -n

### Lab 2: sort & uniq

1. Create file with duplicate names
2. Sort and remove duplicates

### Lab 3: find Practice

1. Find all .txt files in home
2. Find files larger than 50MB

---

## ⚠️ 1️⃣6️⃣ Common Mistakes

- Using uniq without sort
- Forgetting quotes in patterns
- Running find / as root without care
- Accidentally deleting files

---

## 📝 1️⃣7️⃣ Practice Questions

### Basic

1. What does grep do?
2. Difference between find and grep?
3. What is pipe?

### Hands-on

1. Find all .log files in /var.
2. Search word "failed" in a log file.
3. Remove duplicate lines from file.

---

## 🎯 1️⃣8️⃣ Interview & Scenario Questions

1. How do you find a file when you don’t know its location?
2. How do you find all files older than 30 days?
3. How do you search errors in huge log files?
4. How do you delete all .tmp files safely?

---

## 📌 1️⃣9️⃣ Quick Revision Summary

| Task              | Command |
| ----------------- | ------- |
| Read file         | cat     |
| Search text       | grep    |
| Sort data         | sort    |
| Remove duplicates | uniq    |
| Find files        | find    |

---


