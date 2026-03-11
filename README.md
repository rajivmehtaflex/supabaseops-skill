# Supabase Operations Skill

A portable agent skill for Supabase CLI operations. It is packaged in the universal `.agents/skills` layout so it can be reused by tools that follow the shared skill convention, including `skills.sh`-compatible tooling.

## Repository Layout

```text
.agents/
  skills/
    supabaseops/
      SKILL.md
      references/
      evals/
```

The canonical installable skill folder in this repo is `.agents/skills/supabaseops/`.

## Install

### Universal install

Copy `.agents/skills/supabaseops` into your agent's skills directory.

Examples:

- Claude Code: `~/.claude/skills/supabaseops`
- Codex: `~/.codex/skills/supabaseops`
- Any `skills.sh`-compatible tool: its configured skills directory

### Remote install (from GitHub)

```bash
mkdir -p ~/.claude/skills/supabaseops/references && \
curl -sL https://raw.githubusercontent.com/rajivmehtaflex/supabaseops-skill/main/.agents/skills/supabaseops/SKILL.md -o ~/.claude/skills/supabaseops/SKILL.md && \
curl -sL https://raw.githubusercontent.com/rajivmehtaflex/supabaseops-skill/main/.agents/skills/supabaseops/references/cli-map.md -o ~/.claude/skills/supabaseops/references/cli-map.md
```

Or with `wget`:

```bash
mkdir -p ~/.claude/skills/supabaseops/references && \
wget -qO ~/.claude/skills/supabaseops/SKILL.md https://raw.githubusercontent.com/rajivmehtaflex/supabaseops-skill/main/.agents/skills/supabaseops/SKILL.md && \
wget -qO ~/.claude/skills/supabaseops/references/cli-map.md https://raw.githubusercontent.com/rajivmehtaflex/supabaseops-skill/main/.agents/skills/supabaseops/references/cli-map.md
```

### Verify install

```bash
ls ~/.claude/skills/supabaseops/
# Should show: SKILL.md  references/
```

### Manual install (if you have the repo cloned)

```bash
mkdir -p ~/.claude/skills/supabaseops/references
cp .agents/skills/supabaseops/SKILL.md ~/.claude/skills/supabaseops/SKILL.md
cp .agents/skills/supabaseops/references/cli-map.md ~/.claude/skills/supabaseops/references/cli-map.md
```

## Example prompts

Once installed, Claude will use this skill automatically. Try:

1. **New project setup + first migration:**
   > "Set up a new Supabase project locally and create my first migration to add a 'profiles' table with columns: id (uuid, references auth.users), username (text, unique), created_at (timestamptz, default now()). Walk me through everything I need to do."

2. **Deploy an edge function with secrets:**
   > "I need to deploy an edge function called 'send-email' to my Supabase project. The function uses a SendGrid API key that should be stored as a secret. Show me the full workflow."

3. **Pull remote schema and generate TypeScript types:**
   > "My Supabase project already has tables set up remotely. I want to pull the remote database schema into my local project and then generate TypeScript types from it. How do I do this?"

## Contents

- `.agents/skills/supabaseops/SKILL.md` — skill definition loaded by supported agents
- `.agents/skills/supabaseops/references/cli-map.md` — full Supabase CLI command reference
- `.agents/skills/supabaseops/evals/evals.json` — evaluation prompts used to test the skill
