# Install superpm

<details>
<summary><strong>Claude Code</strong></summary>

### Install

```bash
claude plugin marketplace add cskwork/superpm
claude plugin install superpm@superpm
```

Type `/superpm`.

### Verify

```bash
claude plugin list
```

### Update

```bash
claude plugin marketplace update superpm
```

### Uninstall

```bash
claude plugin uninstall superpm
claude plugin marketplace remove superpm
```

</details>

<details>
<summary><strong>Codex</strong></summary>

### Install

```bash
codex plugin marketplace add cskwork/superpm --ref main
codex plugin add superpm@superpm
```

Type `$superpm`.

### Verify

```bash
codex plugin list
```

### Uninstall

```bash
codex plugin remove superpm
codex plugin marketplace remove superpm
```

</details>

<details>
<summary><strong>Gemini CLI</strong></summary>

### Install (extension, always-on)

```bash
gemini extensions install https://github.com/cskwork/superpm
```

### Install (command, opt-in)

```bash
mkdir -p ~/.gemini/commands
curl -fsSL https://raw.githubusercontent.com/cskwork/superpm/main/skills/superpm/agents/gemini.toml \
  -o ~/.gemini/commands/superpm.toml
```

Type `/superpm` in a new session.

### Verify

```bash
gemini extensions list
```

### Uninstall

```bash
gemini extensions uninstall superpm
```

</details>

<details>
<summary><strong>Cursor, OpenCode, Amp, and other agent-skills harnesses</strong></summary>

### Install

```bash
npx skills add cskwork/superpm
npx skills add cskwork/superpm -g
```

Type `/superpm` in a new agent chat.

### Verify

```bash
npx skills list
```

### Update

```bash
npx skills update superpm
```

### Uninstall

```bash
npx skills remove superpm
```

</details>

<details>
<summary><strong>Antigravity (agy)</strong></summary>

### Install

```bash
agy plugin install https://github.com/cskwork/superpm
```

### Verify

```bash
agy plugin list
```

### Uninstall

```bash
agy plugin uninstall superpm
```

</details>
