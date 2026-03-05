# supabaseops skill for Claude Code

A Claude Code skill that provides expert guidance for Supabase CLI operations. When installed, Claude will automatically use this skill whenever you mention Supabase — covering local dev setup, database migrations, edge functions, secrets management, type generation, storage, and remote project management. The skill includes a prerequisites check flow to ensure authentication and project linking are handled correctly before any command runs.

## Install

### Remote install (from GitHub)

```bash
mkdir -p ~/.claude/skills/supabaseops/references && \
curl -sL https://raw.githubusercontent.com/rajivmehtaflex/supabaseops-skill/main/SKILL.md -o ~/.claude/skills/supabaseops/SKILL.md && \
curl -sL https://raw.githubusercontent.com/rajivmehtaflex/supabaseops-skill/main/references/cli-map.md -o ~/.claude/skills/supabaseops/references/cli-map.md
```

Or with `wget`:

```bash
mkdir -p ~/.claude/skills/supabaseops/references && \
wget -qO ~/.claude/skills/supabaseops/SKILL.md https://raw.githubusercontent.com/rajivmehtaflex/supabaseops-skill/main/SKILL.md && \
wget -qO ~/.claude/skills/supabaseops/references/cli-map.md https://raw.githubusercontent.com/rajivmehtaflex/supabaseops-skill/main/references/cli-map.md
```

### Verify install

```bash
ls ~/.claude/skills/supabaseops/
# Should show: SKILL.md  references/
```

### Manual install (if you have the repo cloned)

```bash
mkdir -p ~/.claude/skills/supabaseops/references
cp SKILL.md ~/.claude/skills/supabaseops/SKILL.md
cp references/cli-map.md ~/.claude/skills/supabaseops/references/cli-map.md
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

- `SKILL.md` — skill definition loaded by Claude Code
- `references/cli-map.md` — full Supabase CLI command reference
- `evals/evals.json` — evaluation prompts used to test the skill (100% pass rate on iteration 1)
