# On the FlashyOS mesh

spec-templates is a specification-adjacent property on the FlashyOS mesh — not
a wire format itself, but the scaffolding a new spec repository in this
estate is meant to be authored from.

Its AAO charter is [`flashyos.roles.json`](flashyos.roles.json) — the single
source the mesh handshake and the directory fragment derive from, so two
hand-written files can never disagree. It declares **five roles**, and five
roles are five agents:

| Role | Family | Human approval at/above | What it is accountable for |
|---|---|---|---|
| `template` | governance | HIGH | Publishes and maintains the scaffolding templates and the generation rules a new spec repository in this estate is authored from. |
| `conformance` | engineering | LOW | Runs the checker over the templates themselves, and over anything scaffolded from them, and reports which cases pass rather than a green tick that read nothing. |
| `release` | operations | MEDIUM | Cuts versioned releases of the template set with a changelog entry, so a version says what the templates will refuse and never moves once it ships. |
| `adoption` | growth | LOW | Helps a new spec repository bootstrap from these templates and records how many have, because a template nobody has used is not yet worth keeping. |
| `review` | risk | HIGH | Reviews a proposed change to the templates before it lands, because a change to the scaffold changes every spec repository authored from it afterward. |

`canon` is renamed `template` here — the same adaptation `AgenteLabs/agent-starter`
made, and for the same reason: this repository publishes a pattern for OTHER
repositories to be authored from, not a normative wire format of its own, so
the governing role is "owns the template," not "owns the spec." The other four
roles keep their names from `interface-definitions`' charter because their
jobs — checking, releasing, growing adoption, reviewing change — are the same
shape here, just pointed at a scaffold instead of a schema.

**Five roles, and the FREE tier allows five agents — a coincidence, not a
target.** The role count above comes from dividing this repository's actual
accountability into five distinct jobs; it was not shrunk, or grown, to fit a
plan's agent cap. That this repository's honest division happens to land on
exactly five, matching every other charter drafted in this estate so far, is
worth noting and not worth reading into.

The charter validates against the estate's dependency-free AAO checker. The
vendored `vendor-aao-check.mjs` is **not present until the generator lands**,
so the command below is planned, not runnable here today:

<!-- planned -->
```bash
node vendor-aao-check.mjs validate flashyos.roles.json   # 0 issues
```

**Becoming a live organisation.** The charter is what a live org is
provisioned from. This runs from the flashyos monorepo (`packages/api/…` does
not live in this shell) on a machine that holds `DATABASE_URL`, so it too is
planned rather than runnable here:

<!-- planned -->
```bash
npx tsx packages/api/scripts/provision-org-from-charter.ts \
  --charter flashyos.roles.json --tier FREE
```

The FREE tier allows five agents, which is exactly this charter's five
roles — the same coincidence `interface-definitions` and `agent-starter` both
note, and it is nothing more than a coincidence: the charter was written
against what this repository actually does, not trimmed or padded to fit a
plan cap. Had a sixth distinguishable governance function existed here, the
honest move would have been to raise the tier (`set-org-tier.ts`) rather than
fold two roles into one, or invent a sixth role to use the headroom.

`directory.fragment.json` is this org's `directory/1` node: the org, one
agent per role, and the accountable person.
