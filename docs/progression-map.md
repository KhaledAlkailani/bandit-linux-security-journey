# Progression Map

The Bandit journey can be understood as a progression in the type of question being solved.

## Stage 1 — File Discovery

Typical question:

> Where is the data?

Concepts:

- directories;
- hidden files;
- unusual filenames;
- basic permissions.

## Stage 2 — Data Interpretation

Typical question:

> What is this data and how do I make it readable?

Concepts:

- searching;
- filtering;
- encoding;
- binary data;
- compression.

## Stage 3 — Service Interaction

Typical question:

> Which service is listening and how do I communicate with it correctly?

Concepts:

- SSH;
- TCP;
- TLS;
- service discovery;
- local listeners.

## Stage 4 — Privilege Boundaries

Typical question:

> Which identity can perform this action?

Concepts:

- ownership;
- SUID;
- protected resources;
- effective execution context.

## Stage 5 — Automated Behavior

Typical question:

> What does the system do automatically?

Concepts:

- cron;
- scripts;
- predictable files;
- scheduled privilege.

## Stage 6 — Execution Restrictions

Typical question:

> What is actually controlling my session?

Concepts:

- login shells;
- forced commands;
- pagers/editors;
- environment behavior.

## Stage 7 — Historical Evidence

Typical question:

> What used to exist even if it is not visible now?

Concepts:

- Git history;
- branches;
- tags;
- hooks;
- deleted secrets.

## Overall Shift

```text
Command usage
     ↓
System observation
     ↓
Behavior analysis
     ↓
Security reasoning
```
