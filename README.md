# Triad — Claude Code Skill

**One introduction a day. Before lunch. Two people who share the same ideal client but have adjacent offers.**

That's the Triad. It's the highest-leverage networking ritual you're not doing. You connect two people who aren't competitors but serve the same buyer. They become force multipliers for each other — and both remember you as the person who made it happen.

---

## From Strategy Sprints

The Triad is part of the **Strategy Sprint Method** — a 90-day execution system that helps B2B founders double revenue by finding and fixing their #1 bottleneck.

Most founders network randomly. They collect contacts, attend events, and hope something sticks. The Triad turns networking into a system: one deliberate introduction per day, matched by shared ICP and adjacent offers, tracked so you never repeat.

200+ founders have used Strategy Sprints to add $1M+ in annual revenue. The Triad is how many of them built the partnerships that got them there.

**Want to sprint?** [Book a Strategy Call](https://www.strategysprints.com) | [Watch The Sales Show](https://youtube.com/@salesshow)

---

## Install

```bash
git clone https://github.com/SimonTheSalesBooster/triad.git ~/.claude/skills/triad
```

Or copy `SKILL.md` directly into `~/.claude/commands/triad.md`.

## What It Does

Every time you run `/triad`, Claude:

1. **Scans your network** — reads your Notion Partners database (ICP, Superpower, collaboration history) and Obsidian People folder (expertise, tags, introduction value links)
2. **Checks for warm signals** — searches Gmail (last 30 days) and Google Calendar (last 14 days + next 7) to find who you've recently talked to
3. **Finds the best match** — scores pairs by shared ICP, adjacent offers, pre-flagged connections, and recency of contact
4. **Prevents duplicates** — checks the `Introduced To` field in your Partners database so you never make the same introduction twice
5. **Drafts a Gmail intro** — creates a ready-to-send email draft (under 100 words, specific, warm, references why they should talk)
6. **Logs it** — updates both partner rows in Notion with the introduction details

## What Makes a Triad

A Triad is NOT just any introduction. It has three requirements:

| Requirement | Example |
|---|---|
| **Same ideal client** | Both serve B2B SaaS founders |
| **Adjacent offers** | One does video prospecting, the other does creative direct mail |
| **Non-competing** | They're not fighting for the same budget line |

The magic: when two people serve the same buyer with complementary services, they naturally refer each other. You created that loop.

## Usage

```
/triad
```

No arguments needed. Claude finds the best match, drafts the email, logs it.

### Examples

#### First run — setup
```
/triad
```
Claude reads your Notion Partners database and Obsidian People folder, finds the strongest match, creates a Gmail draft, and updates both partner rows. If a person isn't in your Partners database yet, Claude adds them.

#### Daily habit
```
/triad
```
Run it every morning. Claude picks a new pair each day, skipping anyone you've already introduced. Over 90 days, that's 90 introductions — a network effect most people never build.

#### After a meeting
```
/triad
```
Run it right after a great call. Claude picks up the calendar signal and uses it: "I just spoke with [Name] and immediately thought of you."

#### Check your streak
The report at the end shows your total introduction count. Track it like a habit.

## What You Need

- **Notion** — a Partners database with Name, Email, ICP, and Superpower columns (the skill adds `Introduced To`, `Intro Date`, `Intro Status` columns on first run)
- **Gmail** — connected via Claude's Gmail MCP integration (for drafts and warm signal detection)
- **Google Calendar** — connected via Claude's Calendar MCP integration (for meeting signal detection)
- **Obsidian** (optional) — a People folder with person files containing expertise, tags, and Introduction Value sections

## The Email Format

Every introduction follows the same structure:

```
Hi [Name A], hi [Name B],

I want to connect you two — I think there's a natural fit.

[Name A] — [what Name B does and why it matters to A]

[Name B] — [what Name A does and why it matters to B]

You both [shared ICP]. Different angles, same client.
That's usually where the best partnerships start.

I'll let you two take it from here.

Best,
Simon
```

Under 100 words. No fluff. Specific about WHY.

## Automation

Set it up as a daily launchd agent to run at 08:30:

```bash
# Create plist: ~/Library/LaunchAgents/com.strategysprints.triad.plist
# Schedule: Daily 08:30
# Command: claude -p "/triad"
```

Or just run `/triad` manually each morning before lunch.

## License

MIT
