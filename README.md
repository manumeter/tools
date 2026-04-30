# Tools

```
$ rgit --help
Usage:
  rgit [options] <command> [dir1 [dir2 [...]]]

  Recursively searches all git repos under the given dir(s), or "." if no dir
  is given, and runs the given command on them.

  Git submodules are ignored by all commands. They are considered part of
  their parent repository.

Options:
  -v, --verbose
    Print progress information to stderr.
    Useful to see where update/up is hanging.

  -j, --jobs N
    Process up to N repositories in parallel.
    Default: 8

  -t --timeout SECONDS
    Timeout for git fetch and origin/HEAD detection during update/up.
    Default: 60 seconds.
    Requires "timeout" or "gtimeout" to be installed. If neither exists,
    the timeout cannot be enforced.

  -h, --help
    Show this help.

Commands:
  list, ls
    List all repos as git clone commands.
    This can be used to recreate the same repo directory structure.

  update, up
    Fetch origin, including all remote branches, and safely fast-forward
    local branches where possible.
    Already up-to-date repos produce no output.
    Problems such as fetch failures, local commits, diverged branches or local
    changes preventing a fast-forward are reported.

  status, st
    Print the following status infos:
      - local uncommitted changes
      - untracked files/directories
      - local branches not present on origin
      - local branches that differ from origin
    Clean repos produce no output.
    Does not fetch; it compares against currently known origin/* refs.

  branch-status, bs
    Print a brief summary of the differences between the default origin branch
    and all other known origin branches.
    Repos with no differences between origin branches produce no output.
    Does not fetch; run update/up first if you want fresh origin refs.

  diff, df
    Print local staged and unstaged diffs.
    Repos without local diffs produce no output.
    Untracked files are not shown here; use status/st for those.

  branch-diff, bd
    Print the full diffs between the default origin branch and all other known
    origin branches that have file differences.
    Repos with no differences between origin branches produce no output.
    Does not fetch; run update/up first if you want fresh origin refs.

Examples:
   rgit ls ~/all-repos > ~/git-repos-$(date +%F).sh
   rgit up
   rgit -v up
   rgit -j 8 --fetch-timeout 30 up repos/*
   rgit st
   rgit bs repos/app-* repos/cluster-app-*
```
