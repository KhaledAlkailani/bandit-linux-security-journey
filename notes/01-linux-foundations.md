# Linux Foundations

This section groups the early Bandit work around one core skill: becoming comfortable enough with Linux that navigation and file handling stop being obstacles.

## Concepts Practiced

- directory listing;
- hidden files;
- unusual filenames;
- command parsing;
- relative paths;
- basic file inspection;
- permissions and metadata.

## Examples of What I Learned

### Hidden Files

A normal directory listing does not show hidden entries.

```bash
ls -al
```

This became an early reminder that the visible filesystem is not always the complete filesystem view.

### Filenames That Look Like Options

A filename beginning with characters such as `-` can be interpreted by a command as an option.

Two useful techniques are:

```bash
cat ./<filename>
```

or:

```bash
cat -- <filename>
```

The important concept is not the exact command.

It is that **command-line parsers distinguish between options and operands**, and filenames can influence that parsing.

### File Metadata and Permissions

Later levels made permissions much more important, but the foundation started here:

```bash
ls -al
file <filename>
stat <filename>
```

These commands answer different questions:

- What exists?
- Who owns it?
- What permissions are applied?
- What type of data does the file appear to contain?

## Security Relevance

Linux security work depends heavily on basic filesystem literacy.

A suspicious file may be:

- hidden;
- named to confuse shell parsing;
- unreadable to the current user;
- owned by another user;
- executable under a different context.

If those concepts are not automatic, deeper investigation becomes much slower.

## Main Takeaway

> Before asking which exploit or tool to use, first understand how the operating system is presenting the resource.
