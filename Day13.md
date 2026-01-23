
# 📦 Archiving & Compression in Linux 

## 1️⃣ Introduction to Archiving & Compression

In Linux, we often need to:

- Take backups
- Send multiple files together
- Save disk space

For this we use:

- **Archiving** → Combine many files into one file  
- **Compression** → Reduce file size

Real-life example:

- Archiving = Putting many books into one box  
- Compression = Removing air from the box to make it smaller

---

## 2️⃣ Difference Between Archiving and Compression

| Feature | Archiving | Compression |
|------|-----------|------------|
| Purpose | Combine files | Reduce size |
| File count | Many → One | One → Smaller |
| Example tool | tar | gzip, bzip2, xz |

Important:
> `tar` alone does **not** compress. It only archives.

---

## 3️⃣ Why Archiving is Important

In real systems, archiving is used for:

- Daily backups
- Log rotation
- Transferring projects
- Storing old data

Example:

```bash
# Backup home directory
tar -cvf home_backup.tar /home/user
```

---

## 4️⃣ Introduction to tar Command

`tar` means **Tape Archive**.

Basic syntax:

```bash
tar <options> <archive-name> <files>
```

Common options:

| Option | Meaning |
|------|--------|
| c | create archive |
| x | extract archive |
| v | verbose (show progress) |
| f | file name |
| t | list contents |

---

## 5️⃣ Creating Archives with tar

Create an archive:

```bash
tar -cvf project.tar project/
```

Create archive of multiple files:

```bash
tar -cvf files.tar file1 file2 file3
```

---

## 6️⃣ Extracting Archives with tar

Extract archive:

```bash
tar -xvf project.tar
```

Extract to specific directory:

```bash
tar -xvf project.tar -C /tmp
```

---

## 7️⃣ Viewing Archive Contents

List files inside archive:

```bash
tar -tvf project.tar
```

This does not extract files.

---

## 8️⃣ Introduction to Compression

Compression reduces file size.

Linux supports many compression formats:

| Tool | Extension | Speed | Compression |
|----|-----------|-------|-------------|
| gzip | .gz | Fast | Medium |
| bzip2 | .bz2 | Slow | Better |
| xz | .xz | Slowest | Best |

---

## 9️⃣ gzip and gunzip

Compress a file:

```bash
gzip file.txt
# creates file.txt.gz
```

Decompress:

```bash
gunzip file.txt.gz
```

Keep original file:

```bash
gzip -k file.txt
```

---

## 🔟 bzip2 and bunzip2

Compress:

```bash
bzip2 file.txt
# creates file.txt.bz2
```

Decompress:

```bash
bunzip2 file.txt.bz2
```

---

## 1️⃣1️⃣ xz and unxz

Compress:

```bash
xz file.txt
# creates file.txt.xz
```

Decompress:

```bash
unxz file.txt.xz
```

---

## 1️⃣2️⃣ Combining Archiving and Compression

Most common in real life:

### tar + gzip

Create compressed archive:

```bash
tar -czvf backup.tar.gz /home/user
```

Extract:

```bash
tar -xzvf backup.tar.gz
```

### tar + bzip2

```bash
tar -cjvf backup.tar.bz2 /data
```

### tar + xz

```bash
tar -cJvf backup.tar.xz /data
```

---

## 1️⃣3️⃣ Real-Time Use Cases

1. Take daily backup:

```bash
tar -czvf /backup/etc_$(date +%F).tar.gz /etc
```

2. Compress old logs:

```bash
gzip /var/log/syslog
```

3. Extract a project:

```bash
tar -xzvf project.tar.gz
```

---

## 🧪 1️⃣4️⃣ Hands-on Labs

### Lab 1: Create Archive

1. Create directory testdir
2. Archive it using tar
3. List archive contents

### Lab 2: Compression Practice

1. Compress a text file using gzip
2. Decompress it back

### Lab 3: Combined Practice

1. Create tar.gz of home directory
2. Extract it into /tmp

---

## ⚠️ 1️⃣5️⃣ Common Mistakes

- Forgetting `-f` option
- Mixing order of options
- Compressing already compressed files
- Extracting in wrong directory

---

## 📝 1️⃣6️⃣ Practice Questions

### Basic

1. What is archiving?
2. Difference between tar and gzip?
3. What does `-c` option do?

### Hands-on

1. Create archive of /etc directory.
2. Compress file using bzip2.
3. Extract tar.gz file.

---

## 🎯 1️⃣7️⃣ Interview & Scenario Questions

1. How do you take backup of /var directory?
2. Difference between .tar and .tar.gz?
3. Which compression gives best ratio?
4. How do you view files inside archive without extracting?

---

## 📌 1️⃣8️⃣ Quick Revision Summary

| Task | Command |
|-----|--------|
| Create archive | tar -cvf |
| Extract archive | tar -xvf |
| List contents | tar -tvf |
| gzip compress | gzip |
| gunzip extract | gunzip |
| tar.gz create | tar -czvf |

---



