# AGENTS.md

## Commands
- **Lint**: No automated linter, but ensure YAML frontmatter is valid and Markdown follows consistent headers.
- **Test**: Manual verification of agent/command prompts. Check `opencode.json` for model availability.

## Project Structure
- **Agent Definitions**: `agent/*.md` - Specialized agent personas, toolsets, and system prompts.
- **Command Workflows**: `command/*.md` - Step-by-step workflows for specific CLI commands.
- **Configuration**: `opencode.json` - Global settings for providers and model mappings.

## Code Style
- **Frontmatter**: Every `.md` file must start with YAML frontmatter containing `description`. Agents also require `mode`, `model`, `temperature`, and a `tools` map.
- **Prompts**: Use clear, hierarchical Markdown headers (`#`, `##`, `###`) to structure instructions.
- **Placeholders**: Use `$ARGUMENTS` in command files to denote where user input is injected.
- **Tone**: Keep agent personas professional, direct, and concise.

## Conventions
- **Agent Roles**: Orchestrator agents (like `smart.md`) should prioritize spawning subagents over performing all work themselves.
- **Tool Mapping**: Explicitly enable/disable tools in the YAML frontmatter for each agent.
- **Documentation**: Use `description` in frontmatter to help the orchestrator select the right tool/agent.

## Safety
- **Tool Access**: Be restrictive with `bash` and `patch` tools in subagent definitions unless strictly necessary.
- **Environment**: Agents should assume they are running in a restricted environment but must still follow best practices for non-destructive operations.
