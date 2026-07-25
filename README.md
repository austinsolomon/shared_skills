# shared_skills

Shared Claude Code skills — Firecrawl web toolkit (32 skills) plus `fc` (Firecrawl-powered page fetch).

## Install on a new machine

```sh
git clone https://github.com/austinsolomon/shared_skills.git ~/shared_skills
mkdir -p ~/.claude/skills
for d in ~/shared_skills/skills/*/; do ln -sfn "$d" ~/.claude/skills/"$(basename "$d")"; done
```

Symlinking (rather than copying) means `git pull` in `~/shared_skills` updates every machine's skills in place.

Note: these skills require the Firecrawl CLI / `FIRECRAWL_API_KEY` to be set up on the machine.
