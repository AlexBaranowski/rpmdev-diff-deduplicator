# rpmdev-diff-deduplicator

This repository contains script that is looking for the RPMS (based on name!),
run `rpmdev-diff` and deduplicate. It works only on noarch and source rpms.

# THIS IS WIP - ALL THINGS PRESENTED BELOW ARE NOT IMPLEMENTED!

**I wrote all things below because writing README.md helps to clarify idea what
program actually should be.**

## Usage

Run `./src/rpmdev-diff-deduplicate $PATH_TO_REPOSITORIES` where
`$PATH_TO_REPOSITORIES` might be something like `/build/repos/eurolinux/8/` or
`/build/sources/eurolinux/8`.

Deduplicaton is hardlink based.

### Options

- `-d` or `--dry-run` - run without change

## After usage

After usage you **have to rebuild repodata** , because some rpms might be
deduplicated as promised ;)!

## Tests

Run `./src/tests.py`


## Why?

During EuroLinux 8 build we started with `x86_64` arch. Then we add `aarch64`
arch. Then we started `ppc64le`. That created multiple src.rpms and noarch. To
save space I decided to deduplicate them with this script. 
