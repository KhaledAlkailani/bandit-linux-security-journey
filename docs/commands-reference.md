# Commands Reference

This reference groups commands by the investigative question they help answer.

It is intentionally not organized as “Level X → command”.

---

## What files exist?

```bash
ls
ls -al
find .
```

Use these to understand directory contents, hidden entries, and recursive structure.

---

## What kind of file is this?

```bash
file <filename>
stat <filename>
strings <filename>
```

Questions answered:

- file type;
- metadata;
- readable text inside otherwise unfamiliar data.

---

## How do I safely reference a strange filename?

```bash
cat ./<filename>
cat -- <filename>
```

Useful when a filename resembles a command-line option.

---

## How do I search or filter text?

```bash
grep "<pattern>" <file>
sort <file>
uniq -u
```

Common pattern:

```bash
sort <file> | uniq -u
```

---

## How do I locate files by properties?

Representative `find` concepts:

```bash
find <path> -size <size>
find <path> -user <user>
find <path> -group <group>
find <path> ! -executable
```

Useful when filenames are unknown but metadata is known.

---

## How do I transform encoded or binary data?

Concepts practiced with:

```bash
base64 -d
tr
xxd
file
gzip
bzip2
tar
```

The main workflow is:

```text
Identify format → transform → inspect again
```

---

## How do I connect remotely?

```bash
ssh -p <port> user@host
ssh -i <key> user@host -p <port>
scp -P <port> user@host:<file> .
```

---

## How do I inspect network services?

```bash
nmap -sV -p <range> localhost
ncat <host> <port>
ncat --ssl <host> <port>
openssl s_client -connect <host>:<port>
```

---

## How do I inspect identity and permissions?

```bash
id
whoami
ls -al
```

Useful for understanding current identity, ownership, and special permission bits.

---

## How do I inspect scheduled tasks?

```bash
cat /etc/crontab
ls /etc/cron.d/
cat /etc/cron.d/<job>
cat /usr/bin/<script>
```

---

## How do I inspect Git history beyond the current files?

```bash
git log
git show <commit>
git branch -a
git tag
git show <tag>
git status
```

---

## Reference Principle

> The best command is the one that answers the next investigative question.
