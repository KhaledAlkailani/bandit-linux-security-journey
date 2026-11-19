# Data and File Analysis

Several Bandit levels focused on extracting one useful piece of information from noisy or transformed data.

This is directly relevant to security analysis because logs, artifacts, captures, and suspicious files are often not presented in a clean format.

## Searching Text

### grep

Used to search for a known pattern inside data:

```bash
grep "<pattern>" <file>
```

Useful when the target information is surrounded by many unrelated lines.

## Finding Unique Data

### sort + uniq

```bash
sort <file> | uniq -u
```

This reinforced two concepts at the same time:

1. pipelines;
2. transforming data before filtering it.

`uniq` works on adjacent lines, so sorting first can be essential.

## Extracting Human-Readable Content

### strings

```bash
strings <file>
```

Useful when a file contains binary or non-printable content but may still include meaningful text.

In real investigations, the same idea can help with:

- binaries;
- memory artifacts;
- unknown files;
- packet payloads.

## Encoding and Transformation

The progression included decoding and character translation.

Examples of concepts practiced:

- Base64 decoding;
- character rotation;
- reversing encoded representations.

The important lesson was to identify whether data is:

- encoded;
- compressed;
- binary;
- encrypted.

Those are different problems.

## Compression and File-Type Identification

One of the more useful exercises required repeatedly identifying a file type and applying the correct decompression method.

Representative workflow:

```text
Inspect file type
      ↓
Rename / prepare file if needed
      ↓
Decompress
      ↓
Inspect again
      ↓
Repeat
```

Tools included concepts around:

- `xxd`
- `file`
- `gzip`
- `bzip2`
- `tar`

## Security Relevance

Security evidence frequently needs transformation before analysis.

For example:

```text
Compressed log
   ↓
Extract
   ↓
Decode
   ↓
Search
   ↓
Correlate
```

The useful skill is not memorizing every decompression command.

It is recognizing the data state and choosing the next operation based on evidence.

## Main Takeaway

> When data looks unreadable, first determine what kind of unreadable it is.
