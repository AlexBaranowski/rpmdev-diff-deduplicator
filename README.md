# rpmdev-diff-deduplicator
This repository contains a script looking for the RPMS (based on name!), run
`rpmdev-diff` and deduplicate. It works only on noarch and source RPMs.


## Usage
Run `./src/rpmdev-diff-deduplicate $PATH_TO_REPOSITORIES` where
`$PATH_TO_REPOSITORIES` might be something like `/build/repos/eurolinux/8/` or
`/build/sources/eurolinux/8`.


Deduplication is hardlink based.

## Options
 - `-d` or `--dryrun` - dry run
 - `-v` or `--verbose` - run in verbose mode

# After usage

After usage, you have to rebuild repodata, because some RPMs might be
deduplicated as promised ;)!

# Limitations

- Currently, all RPMs are compared with the first occurrence on the file
  system.
- Currently, only hard links are supported. That means that files must be on the
  same filesystem (there is check for that).

## Why?

During EuroLinux 8 build, we started with x86_64 arch. Then we add aarch64
arch. Then we started ppc64le. That created multiple source RPMs and noarch
RPMs. To save disk space, I decided to deduplicate them with this script.
