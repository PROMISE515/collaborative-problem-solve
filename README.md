# Collaborative Problem Solve

A Codex Skill and two custom agents for resolving difficult project problems with a human in the decision loop.

`sol_collaborator` owns framing, evidence synthesis, options, and verification. It can call `luna_diagnostician` for narrowly scoped research, reproduction, or counterexample checks. The user chooses the direction at meaningful decision points; the agents do not silently convert a hypothesis into a final answer.

## Contents

```text
.codex/agents/                         Sol and Luna custom-agent profiles
.agents/skills/collaborative-problem-solve/  Explicitly invoked workflow
examples/                               Sample prompt
```

## Install in Codex

Clone this repository, then link the individual profiles and Skill into Codex discovery locations. The commands fail rather than overwrite an existing same-named configuration.

```bash
mkdir -p "$HOME/.codex/agents" "$HOME/.agents/skills"
for agent in "$PWD"/.codex/agents/*.toml; do
  ln -s "$agent" "$HOME/.codex/agents/"
done
ln -s "$PWD/.agents/skills/collaborative-problem-solve" "$HOME/.agents/skills/collaborative-problem-solve"
```

Restart Codex if the agent or Skill list does not refresh. Invoke it explicitly:

```text
Use $collaborative-problem-solve to work with me on this project problem: …
```

## Operating contract

1. Separate facts, assumptions, constraints, and unknowns.
2. Gather direct safe evidence; call at most two Luna diagnostics per decision cycle.
3. Offer reversible options with evidence, confidence, risk, and the smallest useful test.
4. Wait for the user before destructive, costly, externally visible, or scope-expanding actions.
5. Compare observed and expected results. Revise assumptions when they diverge.

For a project already owned by a Terra-Luna pod, this collaboration loop is an escalation process. It does not transfer primary project ownership or primary-memory write authority.

## License

MIT. See [LICENSE](LICENSE).
