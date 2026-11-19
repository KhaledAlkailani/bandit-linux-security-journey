# Permissions and Privilege

Some of the most useful Bandit levels involved Linux privilege boundaries rather than file discovery.

## SUID

A SUID executable can run with the effective privileges of the file owner rather than only the privileges of the user who launched it.

This distinction became visible by inspecting permissions and execution behavior.

Representative checks:

```bash
ls -al
id
whoami
```

## Effective Execution Context

The important question is not always:

> Who typed the command?

It may instead be:

> Under which identity is the resulting process executing?

That difference is fundamental to understanding:

- privileged helper programs;
- SUID binaries;
- service accounts;
- scheduled jobs;
- application processes.

## Protected Resources

Some levels intentionally placed useful data in locations the current user could not read directly.

The challenge was to understand whether another executable or execution path had access.

That creates a security model like:

```text
User A
  │
  ├── cannot read protected file
  │
  └── can execute helper owned by User B
            ↓
       helper runs as User B
            ↓
       protected resource becomes reachable
```

## Security Relevance

This maps directly to privilege-escalation reasoning.

A permission issue is rarely just:

> “This file has mode 4755.”

The more useful questions are:

- Who owns it?
- Who can execute it?
- What can it do?
- Can its arguments or environment be influenced?
- Which protected resources can it reach?

## Main Takeaway

> Privilege is about execution context and reachable actions, not only usernames.
