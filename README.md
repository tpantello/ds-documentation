# Design Standards

Source of truth for Accutech's Design System documentation.
This repo drives AI queryability, developer linting, and human
documentation from a single set of structured files.

## Structure

- `/components` — one folder per component, four files each
- `/patterns` — page-level layout and composition standards
- `/tokens` — design token documentation and standards
- `/_schema` — master JSON schema all component files follow

## File Types Per Component

| File | Owner | Purpose |
|---|---|---|
| `*.standard.md` | Design team | UX standards, when to use, rules, prose |
| `*.api.md` | Auto-generated | Technical API docs, props, slots, examples |
| `*.json` | Auto-generated | Machine-readable, feeds MCP + AI + linter |
| `*.linting.json` | Dev team | Custom and override lint rules |

## How It Works

- AI tools (Claude, Copilot, ChatGPT) query the JSON and Markdown files
- The ESLint plugin reads JSON files to enforce standards in Vue components
- The GitHub Action regenerates `*.api.md` and `*.json` when component
  code changes, and opens a PR for review
- Human prose in `*.standard.md` is manually maintained and never
  overwritten by automation

## Contributing

- **UX standards changes** → edit `*.standard.md` directly, open a PR
- **Custom lint rules** → edit `*.linting.json`, open a PR
- **API doc changes** → edit the source Vue component, the Action handles the rest
