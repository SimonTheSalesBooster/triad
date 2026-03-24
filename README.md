# One Introduction a Day. 90 Introductions in 90 Days. A Network That Refers Itself.

> Connect two people who serve the same buyer with complementary offers. They become force multipliers for each other... and both remember you as the person who made it happen.

## What makes a Triad

Not just any introduction. Three requirements:

| Requirement | Example |
|---|---|
| **Same ideal client** | Both serve B2B SaaS founders |
| **Adjacent offers** | One does video prospecting, the other does creative direct mail |
| **Non-competing** | Not fighting for the same budget line |

When two people serve the same buyer with complementary services, they naturally refer each other. You created that loop.

---

## What `/triad` does

1. **Scans your network** — Notion Partners database (ICP, Superpower, collab history) + Obsidian People folder
2. **Checks warm signals** — Gmail (last 30 days) + Calendar (last 14 days + next 7)
3. **Finds the best match** — scores by shared ICP, adjacent offers, recency of contact
4. **Prevents duplicates** — checks `Introduced To` field so you never repeat
5. **Drafts the intro** — a Gmail draft, under 100 words, specific about WHY they should talk
6. **Logs it** — updates both partner rows in Notion

---

## The email format

```
Hi [Name A], hi [Name B],

I want to connect you two — I think there's a natural fit.

[Name A] — [what B does and why it matters to A]
[Name B] — [what A does and why it matters to B]

You both [shared ICP]. Different angles, same client.
That's usually where the best partnerships start.

I'll let you two take it from here.

Best,
Simon
```

Under 100 words. Specific. No fluff.

---

## Run it

```
/triad
```

No arguments. Claude finds the best match, drafts the email, logs it.

### Install

```bash
git clone https://github.com/SimonTheSalesBooster/triad.git ~/.claude/skills/triad
```

Or copy `SKILL.md` to `~/.claude/commands/triad.md`.

### Requires

- Notion Partners database (Name, Email, ICP, Superpower)
- Gmail (for drafts and warm signal detection)
- Google Calendar (for meeting signals)
- Obsidian People folder (optional)

---

## About

Built by Simon Severino... author of Strategy Sprints and Time Freedom with Jay Abraham. Added over $2 Billion in sales to B2B clients in finance, software, and consulting.

Part of the [Strategy Sprints](https://www.strategysprints.com) open-source skill suite. Pairs with [/4habits](https://github.com/SimonTheSalesBooster/4habits), [/deals](https://github.com/SimonTheSalesBooster/deals), and [/ogilvy](https://github.com/SimonTheSalesBooster/ogilvy).

*keep rolling, Simon & The Sprinters*
