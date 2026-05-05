# Tools

```
$ de --help
usage: de [-h] {en,fr,es,it,ch,ru,pt,pl} word

Translate a word from or to german with dict.leo.org.

positional arguments:
  {en,fr,es,it,ch,ru,pt,pl}
                        language to translate from or to german
  word                  word(s) to translate

options:
  -h, --help            show this help message and exit
```

```
$ mdj2pdf --help
usage: mdj2pdf [-h] file

Convert a jinja2 templated markdown file into a PDF. Use the YAML metadata
block (https://pandoc.org/MANUAL.html#extension-yaml_metadata_block) to add
variables for templating.

positional arguments:
  file        jinja2 templated markdown file with yaml metadata block

options:
  -h, --help  show this help message and exit
```

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

  list-diff, ld FILE
    Generate a diff patch that updates FILE to match the repos currently
    found under the given dir(s). FILE must have the same format as list/ls
    output, but the line order and comments in FILE (lines starting with #)
    are ignored.

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
   rgit ld ~/git-repos-2025-01-01.sh ~/all-repos
   rgit up
   rgit -v up
   rgit -j 8 --fetch-timeout 30 up repos/*
   rgit st
   rgit bs repos/app-* repos/cluster-app-*
```

```
$ ssh-keyup --help
Usage:
  ssh-keyup [-h|--help] [-d|--delete] [user@](host|host.domain|ip)

Description:
  This script uses ssh-keygen to remove entries from ~/.ssh/known_hosts
  and ssh-keyscan to retrieve current keys and write them back to
  ~/.ssh/known_hosts.

  The script tries to resolve this three identities from the given name:
  - all IP (v4 and v6) addresses (DNS A and AAAA records)
  - all fully qualified host names (DNS PTR records)
  - the unqualified host names (from the above)
 
  It will then remove/update all entries from this list. But before
  doing anything, it checks if the host is reachable on port 22 (except
  if -d or --delete is used).

  The user part of the string will always be ignored (this is only for
  convenience to allow copy-paste from the ssh command).

Options:
  -h, --help
    Print usage on one line and exit.
  -m, --man
    Print this detailed help and exit.
  -d, --delete
    Skip check if the host is running SSH and only delete all entries
    in known_hosts instead of replacing them by new ones.

Known Issues:
  Only works if SSH is running on port 22 and the logic may fail in
  environments where conflicting unqualified host names exist.
```
