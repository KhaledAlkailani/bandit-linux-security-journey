# Lessons Learned

The most useful outcome from Bandit was not a list of Linux commands.

It was a change in how I approached unfamiliar systems.

## 1. Start With Observation

Before trying a complex technique, inspect:

- directory contents;
- ownership;
- permissions;
- file types;
- processes or scripts involved.

Simple evidence often explains the path forward.

## 2. Syntax Can Be Security-Relevant

A filename that looks like an option can change command behavior.

Understanding parsing rules matters because input interpretation is part of the security boundary.

## 3. “Unreadable” Is Not One Problem

A file may be:

- encoded;
- compressed;
- binary;
- encrypted;
- permission-restricted.

Those require different responses.

## 4. Identity Matters More Than the Command Name

Two identical commands may have very different impact when executed under different effective identities.

This became especially clear with SUID and cron.

## 5. Automation Creates Trust Relationships

A scheduled process may trust:

- a writable directory;
- predictable input;
- a temporary file;
- another user's script.

That trust can become a security weakness.

## 6. Restrictions Need to Be Evaluated as Systems

A restricted shell can still expose another program that launches a shell.

Security controls should be evaluated by capability, not by the appearance of restriction.

## 7. Git Remembers More Than the Working Tree

A removed secret may still exist in:

- commits;
- branches;
- tags.

Secret removal therefore requires more than editing the current file.

## 8. The Question Improved Over Time

Early:

> Which command finds the answer?

Later:

> Which process, identity, or system behavior makes the answer reachable?

That shift is the part of the journey that transfers most directly to real security work.
