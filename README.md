# Gauntlet Prompt

A Codex skill that turns a rough task request into a complete, ready-to-run **Gauntlet Loop prompt**. It asks only the clarification questions that materially affect the result, then produces a prompt an agent can use to build, inspect, critique, and improve a real deliverable.

The skill creates the prompt; it does not execute the project described by that prompt.

## What it does

- Uses the context already provided, so you do not have to repeat yourself.
- Clarifies the outcome, scope, constraints, available resources, and quality bar.
- Turns vague goals into observable acceptance criteria and appropriate verification steps.
- Includes independent builders and reviewers when the environment supports them and the task benefits from them.
- Sets a practical stopping rule so the improvement loop is bounded.
- Responds in the language you use, including Spanish or English.

## Install in Codex

You need Git and a version of Codex that supports local skills. Clone this repository into your personal skills directory:

```sh
mkdir -p ~/.agents/skills
git clone https://github.com/drodri-es/gauntlet-prompt-skill.git ~/.agents/skills/gauntlet-prompt
```

Codex detects local skills automatically. If the skill does not appear, restart Codex. To update it later:

```sh
git -C ~/.agents/skills/gauntlet-prompt pull
```

You can also ask Codex's `$skill-installer` to install the skill from this repository once it is published. See the [official skill documentation](https://learn.chatgpt.com/docs/build-skills) for other installation scopes.

## Use it

Invoke the skill explicitly in Codex:

```text
$gauntlet-prompt Turn this idea into a complete prompt: build a small mobile-friendly app to track a basketball game.
```

The skill will ask focused follow-up questions if important details are missing. Once the request is complete, it returns a copyable prompt for an agentic coding or creation environment. Codex may also select the skill automatically when your request matches its description.

## Repository contents

- [`SKILL.md`](SKILL.md): the workflow and output instructions.
- [`agents/openai.yaml`](agents/openai.yaml): display name, description, and invocation metadata.

This is an instruction-only skill. It requires no API key, external service, or runtime dependency beyond a compatible skill host.

## License

MIT. See [`LICENSE`](LICENSE).
