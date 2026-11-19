# Automation and Cron

Several Bandit levels used cron jobs to demonstrate how scheduled execution creates trust relationships between users, scripts, files, and temporary directories.

## Cron Basics

Cron runs commands on a schedule.

A standard cron format includes:

```text
minute hour day-of-month month day-of-week command
```

The Bandit exercises required inspecting:

- `/etc/crontab`
- `/etc/cron.d/`
- scripts referenced by cron jobs.

## Scheduled Execution

The key investigation pattern was:

```text
Find scheduled job
      ↓
Identify execution user
      ↓
Inspect referenced script
      ↓
Understand file operations
      ↓
Determine whether output or input is reachable
```

## Predictable Temporary Files

One task generated a filename using deterministic logic.

Once the naming logic was understood, the file location could be predicted.

The security lesson is broader:

> A hidden path is not a security control if the path can be derived predictably.

## Shared Execution Directories

Another task involved a scheduled job that executed scripts from a shared directory.

This demonstrated a dangerous trust relationship:

```text
Writable directory
      ↓
Privileged scheduled process
      ↓
Automatic execution
```

In a real environment, this pattern can become a privilege-escalation path.

## Security Relevance

Automation often runs with more privilege than interactive users.

That means a weak script, writable path, predictable file, or unsafe temporary directory can become much more important than it first appears.

Useful questions include:

- Who owns the cron job?
- Which user executes it?
- Can another user modify its inputs?
- Are temporary files predictable?
- Are scripts or directories writable?
- Does the job expose sensitive output?

## Main Takeaway

> Scheduled tasks are security boundaries because they connect time, identity, and execution.
