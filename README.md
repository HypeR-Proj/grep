<!--
SPDX-FileCopyrightText: 2026 roolrz
SPDX-License-Identifier: Apache-2.0
-->

# grep

Line-oriented regular-expression search for files and standard input.

Matching uses the Rust regex engine; clap owns command parsing. The executable reads
through the Rust standard library and writes results incrementally.

See the [implementation entry](src/lib.rs) and [component declaration](component.json)
for the public interfaces, build dependencies and delivered artifacts.

## Usage

In a Native session with the required capabilities:

```sh
grep pattern /etc/fstab
grep --help
```

## Boundaries

Exit status is 0 for a match, 1 for no match and 2 for an error. The supported pattern
syntax is the Rust regex syntax, not every GNU grep regular-expression extension.

## Build and test

Use this checkout inside the [repo-managed workspace](https://github.com/HypeR-Proj/HypeR).
From this repository directory:

```sh
make
make test
```

An absolute `OUT=/path/to/out` selects a shared output directory. The module
entry delegates to build/system, which prepares the installed SDK and declared
dependencies. Native binaries require HypeR; host module checks cover the tests
selected by component.json. A standalone clone does not contain the workspace’s
other source repositories or Native SDK.
