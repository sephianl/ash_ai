<!--
SPDX-FileCopyrightText: 2024 ash_ai contributors <https://github.com/ash-project/ash_ai/graphs/contributors>

SPDX-License-Identifier: MIT
-->

@AGENTS.md

# The sephianl fork

`main` mirrors `upstream/main` exactly; never commit to it. `sephia` is upstream plus
our patches as a rebased stack, one commit per concern: `git log main..sephia` is the
list, so do not keep a second one here.

- **Never merge upstream into `sephia`.** Run `fork/sync`, which rebases. Merges bury the
  patches, and a patch upstream later accepts no longer drops out by itself.
- **Change a patch with `git commit --fixup <its commit>`**, then
  `git rebase -i --autosquash upstream/main`. A new commit is a new patch; only add one
  for a new concern.
- **Upstream PRs branch from `main`, never from `sephia`**, or they carry the whole stack.
- **Zelo pins `sephia-*` tags, not branches or bare SHAs.** Every force-push orphans the
  previous `sephia` commits, and GitHub eventually garbage-collects anything a tag does
  not hold.
- **Fork-only files live in paths upstream does not have** (this file, `fork/`), so a
  sync never conflicts on them. If upstream adds a `CLAUDE.md`, move this section to
  `fork/README.md`.
