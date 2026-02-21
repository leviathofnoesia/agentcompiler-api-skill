# AgentCompiler API Skill

Public skill bundle for installing AgentCompiler API guidance into agent toolchains.

## Files
- `SKILL.md` - skill definition and usage guidance

## Hosted Docs`n- Public docs/interface repo: https://github.com/leviathofnoesia/AgentCompiler`n- Hosted API base: https://agentcompilerapi.up.railway.app`n- Hosted dashboard: https://agentcompilerapi.up.railway.app/dashboard/`n`n## Install (skills.sh)

```bash
npx skills add leviathofnoesia/agentcompiler-api-skill
```

## Install (ClawHub)

```bash
clawhub install agentcompiler-api-skill
```

## Publish To ClawHub (from this folder)

```bash
# 1) Authenticate
clawhub login

# 2) Publish v1
clawhub publish . --slug agentcompiler-api-skill --name "AgentCompiler API Skill" --version 1.0.0 --tags latest
```

## Update Release (ClawHub)

```bash
# bump semver each publish
clawhub publish . --slug agentcompiler-api-skill --name "AgentCompiler API Skill" --version 1.0.1 --changelog "docs: improve endpoint examples" --tags latest
```

## Create The Skill-Only GitHub Repo

```bash
# run from repository root
mkdir -p temp-skill-repo
cp -r skill-public/agentcompiler-api-skill/* temp-skill-repo/
cd temp-skill-repo

git init
git add .
git commit -m "feat: initial AgentCompiler API skill"
git branch -M main
git remote add origin https://github.com/leviathofnoesia/agentcompiler-api-skill.git
git push -u origin main
```

## Notes
- Keep this repo skill-only (no app source code).
- For skills.sh discoverability, installs with telemetry improve ranking.
- For ClawHub, publish from the skill folder containing `SKILL.md`.
