# Git Security and Repository History

The final Bandit stages moved from Linux host behavior into Git and source-control security.

## Cloning Over SSH

The exercises reinforced Git as a networked system, not just a local folder.

Representative concept:

```bash
git clone ssh://user@host:<port>/<repository-path>
```

## Commit History

One level contained sensitive information in an earlier commit that had been removed from the current file.

Useful commands included concepts around:

```bash
git log
git show <commit>
```

This demonstrated a critical security principle:

> Removing a secret from the latest version does not remove it from Git history.

## Branches

Another exercise required looking beyond the default branch.

```bash
git branch -a
```

The useful lesson is that sensitive or unfinished information may remain in:

- remote branches;
- development branches;
- abandoned branches.

## Tags

A later challenge stored useful information in a Git tag.

```bash
git tag
git show <tag>
```

This reinforced that Git objects extend beyond the working tree and visible branches.

## .gitignore

One task required understanding that ignored files are not automatically impossible to commit.

The distinction between:

- ignored;
- untracked;
- staged;
- committed;

became practical.

## Server-Side Hooks

The final Git-oriented task involved remote validation through a server-side hook.

This illustrated that:

```text
Local repository
      ↓
git push
      ↓
Remote repository
      ↓
Server-side hook
      ↓
Validation / policy
```

## Security Relevance

Git repositories can leak sensitive information through:

- commit history;
- branches;
- tags;
- accidentally committed secrets;
- generated files;
- weak repository hygiene.

A repository should therefore be treated as an evidence source, not only as the latest version of the code.

## Main Takeaway

> The working tree is only one view of repository history.
