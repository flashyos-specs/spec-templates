# spec-templates

```
        ██
       ██
      ██████
        ██
       ██
      ██
```

[![CI](https://github.com/flashyos-specs/spec-templates/actions/workflows/ci.yml/badge.svg)](https://github.com/flashyos-specs/spec-templates/actions/workflows/ci.yml) [![License](https://img.shields.io/badge/licence-Apache--2.0-blue)](LICENSE)

**The scaffolding a new spec repository in this estate is authored from.**

Apache-2.0 templates: the README, the MESH charter, the shared hygiene files, and the test that keeps a shell honest about what does and does not run yet. Every spec repository that has shipped so far — `flashyos-specs/interface-definitions`, `AgenteLabs/agent-starter` — was drafted by hand, against whichever sibling happened to be checked out at the time. This repository exists so that stops being true.

> **Not released yet.** A spec package carried out of the flashyos monorepo keeps its real commit history, which is a decision rather than a build — but that is not quite this repository's situation. As of this commit there is no single existing package to carry out: this shell generalises a hand process already run twice, rather than extracting code that already runs somewhere. See [Status](#status).

## Using it

> **Planned — not present until the generator is written.** The `generate.mjs`
> (or equivalent) and the `templates/` tree the commands below read do **not**
> exist in this repository yet, so nothing in this section is runnable today.
> This section describes how the templates will be used once that tool is
> built — see [Status](#status).

The design is that scaffolding a new spec repository becomes one command, run
once, against a target directory —

<!-- planned -->
```bash
git clone https://github.com/flashyos-specs/spec-templates && cd spec-templates
node generate.mjs --name my-new-spec --org flashyos-specs
# writes README.md, MESH.md, flashyos.roles.json, directory.fragment.json,
# LICENSE, SECURITY.md, CODE_OF_CONDUCT.md, CONTRIBUTING.md, CHANGELOG.md,
# .editorconfig, .gitignore, .nvmrc, test/honesty.test.mjs into ./my-new-spec
```

Every file it would write is a file this repository already carries, so the
generator cannot drift from what a maintainer fills in by hand today — it
would be filling in the same files, the same way.

## What will be here

The scaffolding templates a new spec repository in this estate is authored
from: the honest "not yet migrated" shell pattern itself (this README's and
[MESH.md](MESH.md)'s own shape), the AAO charter shape, the hygiene files
shared across an org (LICENSE, SECURITY.md, CODE_OF_CONDUCT.md,
CONTRIBUTING.md), and the `test/honesty.test.mjs` pattern that refuses an
unmarked code block pointing at a file that is not there yet. A generator
script is the planned difference from today: right now each shell is drafted
by hand, by whoever is on duty, against whichever sibling they happened to
fetch — exactly the kind of thing this estate's own rules say not to repeat
from memory elsewhere.

## The invariants

Everything here follows from these, each enforced by something rather than
promised.

| Invariant | Why | Enforced by |
| --- | --- | --- |
| **A shell's docs never claim a command is runnable before the files it reads exist** | A README that lies about what runs is the drift this estate exists to refuse elsewhere | `test/honesty.test.mjs`'s unmarked-block check |
| **The hygiene files are one house template, not a rewrite per repository** | A licence or a code of conduct reworded per repository is one nobody actually agreed to twice | Verbatim, same-org copy today; a drift test once a generator exists |
| **A template nobody has used is not yet worth keeping** | A scaffold three people have each forked by hand and two have abandoned is a rumour, not a template | The `adoption` role's own measure |

## It works alone

No account, no API key, no telemetry — and, once the generator exists, no
network call either: every file it writes will be read from this repository,
never fetched from a running service. That is the same discipline
`interface-definitions` states for its own checker, extended to the thing
that would otherwise be fetched and adapted by hand.

## What spec-templates is not

- **Not a spec.** It carries no `profiles/`, no schema, no conformance
  corpus. It carries the paperwork a spec repository needs before any of
  that lands.
- **Not a registry of the specs it has scaffolded.** `directory.fragment.json`
  here is this repository's own node, not an index of repositories it helped
  create — that belongs to the estate directory, never to this shell.
- **Not adopted.** As at this commit, no spec repository in this estate has
  been scaffolded from a generator that lives here, because the generator
  does not exist yet. `interface-definitions` and `agent-starter` were each
  drafted by hand — the gap this repository exists to close.

## Status

**The generator is not here yet.** What is here is the licence, the security
policy, the AAO charter and the direction. Unlike a spec package carried out
of the flashyos monorepo with its real commit history, there is no single
existing source to extract here: the thing to build is new tooling — a
reusable version of the hand process that produced this very shell. A roadmap
item for that generator is filed alongside this draft, separately from the
history-preserving carry-outs the other shells describe.

## Contributing

**The most useful thing you can send is a spec shell this estate had to draft
by hand, with a note on where this template guessed wrong.** Every mismatch a
human catches by hand is a line the eventual generator needs to get right
once, rather than a reviewer needing to catch forever.

Sign-off rather than a copyright assignment — see
[CONTRIBUTING.md](CONTRIBUTING.md). There is no CLA.

## Licence

[Apache-2.0](LICENSE), copyright Flashy Labs. The templates are open; fork
them, and tell us where yours diverged from what a real spec repository
needed.

## Precedent

This shell was itself drafted by hand against
[`flashyos-specs/interface-definitions`](https://github.com/flashyos-specs/interface-definitions),
the same way `AgenteLabs/agent-starter` was. That is not a coincidence worth
hiding — it is the exact gap this repository exists to close.
