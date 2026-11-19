# Restricted Shells and Execution Context

Some later Bandit levels were less about finding data and more about understanding how the login environment itself had been restricted.

## Modified Shell Startup

One level terminated the session through shell startup behavior.

Instead of accepting the default login path, the exercise required thinking about whether SSH could execute another command or shell directly.

The useful concept was:

```text
SSH connection
      ↓
Default login behavior
      ↓
Startup file / forced behavior
      ↓
Alternative execution path?
```

## Forced Programs

Another user account did not receive a normal shell at all.

The login configuration launched a pager instead.

Understanding the configured shell and the program being executed was more important than repeatedly trying normal shell commands.

## Pagers and Editors

Interactive programs can sometimes expose additional execution functionality.

The exercise reinforced an important defensive idea:

> Restricting a shell is not enough if another permitted program can start a shell or execute arbitrary commands.

## Uppercase / Restricted Command Environment

The final progression included an environment that transformed normal input before execution.

The solution required understanding shell expansion and process context rather than relying on ordinary command names.

This was a strong example of how:

```text
Interface restriction
      ≠
Complete execution restriction
```

## Security Relevance

Restricted shells, forced commands, jump hosts, kiosk environments, and limited administrative interfaces all rely on controlling execution paths.

When evaluating one, useful questions include:

- What process actually receives input?
- What expansion happens before validation?
- Can another program be launched?
- Are editors or pagers allowed?
- Can environment variables influence execution?
- Does the restriction control commands or the underlying capability?

## Main Takeaway

> A control is only as strong as the alternate execution paths it leaves available.
