# @topy-ai/cpo-skills

The [TOPY.AI](https://topy.ai) AI CPO skills for **Claude Code, Codex, Pi, Cursor, Gemini CLI, OpenCode, GitHub Copilot, Windsurf** and other coding agents: 19 skills that decide what a small company builds and prove it worked, the way a senior CPO would — a weekly product review, feedback triaged with clear rules and every sender answered, de-identified user research, a PMF survey, positioning, RICE priorities, a now/next/later roadmap, PRDs with a success metric, a build-or-not check before the AI CTO, pre-registered experiments read without peeking and a decision log with falsifiers — powered by the TOPY.AI CPO MCP server.

```sh
npx @topy-ai/cpo-skills install                  # this project, for the agents set up here
npx @topy-ai/cpo-skills install -g               # your user: every project
npx @topy-ai/cpo-skills install -g -a codex,pi   # pick the agents
npx @topy-ai/cpo-skills install --mcp            # also add the CPO MCP server to .mcp.json (Claude Code)
```

Pi users can also install it as a Pi package: `pi install npm:@topy-ai/cpo-skills`.

## Agents

| Agent | Skills | MCP server |
|---|---|---|
| **Claude Code** | `npx @topy-ai/cpo-skills install -a claude`, or the plugin marketplace | `install --mcp` writes `.mcp.json`, or the `topy-ai-cpo` plugin |
| **Codex** | `npx @topy-ai/cpo-skills install -a codex`, or `codex plugin marketplace add TOPY-AI-LTD/TOPY-AI-CPO-Skills` | `codex mcp add topy-cpo --url https://topy.ai/mcp/cpo` |
| **Pi** | `pi install npm:@topy-ai/cpo-skills` | `npx -y @topy-ai/cpo-mcp` |
| **Cursor, Gemini CLI, OpenCode, Copilot, Windsurf and others** | `npx @topy-ai/cpo-skills install -a <agent>` | Remote URL `https://topy.ai/mcp/cpo` |
| **Claude.ai, Claude Desktop, ChatGPT** | Upload a skill folder as a zip | Custom connector `https://topy.ai/mcp/cpo` |

`npx @topy-ai/cpo-skills agents` prints the supported agents and marks the ones found on your machine. The install record lives in `<project>/.topy-ai/cpo-skills-install.json`, or `~/.config/topy/cpo-skills-install.json` for the user scope (`TOPY_HOME`). Commit the project's skill folders and `.topy-ai/` to share the skills with your team.

## Choose skills

```sh
npx @topy-ai/cpo-skills list                                              # every skill, by category
npx @topy-ai/cpo-skills install --category feedback,experiments          # categories (or plugin names like topy-ai-cpo-feedback)
npx @topy-ai/cpo-skills install topy-cpo-prd topy-cpo-experiment-read  # single skills
```

Categories: `core` (connect, goals, weekly product review, daily watch — always installed), `feedback`, `discovery`, `planning`, `experiments`, `decisions`.

## The MCP server

`https://topy.ai/mcp/cpo` — the same TOPY.AI account and sign-in (OAuth) as the AI CEO, CFO, COO, CSO and CRO; only the accounts that own the OneMan operation see its product records. For scheduled agents, an API key as `TOPY_API_KEY`.

```sh
npx @topy-ai/cpo-skills mcp -g     # prints the commands for Claude Code, Codex, Gemini CLI, Cursor and Pi
```

## Update and remove

```sh
npx @topy-ai/cpo-skills@latest update                      # this project (-g for your user)
npx @topy-ai/cpo-skills remove topy-cpo-roadmap            # or --all
npx @topy-ai/cpo-skills doctor
```

Files you edited are kept on update and remove unless you pass `--force`. Every command accepts `--dry-run`. The CEO, CFO, COO, CSO, CRO and CPO skill packages install side by side; each keeps its own record.

## Without the installer

```sh
git clone --depth 1 https://github.com/TOPY-AI-LTD/TOPY-AI-CPO-Skills.git
mkdir -p ~/.agents/skills
cp -R TOPY-AI-CPO-Skills/plugins/*/skills/* ~/.agents/skills/
```

Or `npx skills add TOPY-AI-LTD/TOPY-AI-CPO-Skills -a <agent>`. Claude Code plugins: `/plugin marketplace add TOPY-AI-LTD/TOPY-AI-CPO-Skills`, then `/plugin install topy-ai-cpo-all@topy-ai-cpo`.

Source, skills index and changelog: [TOPY-AI-LTD/TOPY-AI-CPO-Skills](https://github.com/TOPY-AI-LTD/TOPY-AI-CPO-Skills).
