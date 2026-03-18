Daily Triad Introduction — connect two people in your network who share the same ideal client but have adjacent offers. Part of the Strategy Sprint Method by Simon Severino.

---

# The Triad — Daily Introduction Ritual

> **The rule:** One email introduction every day before lunch.
> **The principle:** Connect two people who sell to the SAME ideal client but have ADJACENT (non-competing) offers. Example: both sell to food franchises — one does accounting, the other builds websites. They're not competitors. They're force multipliers for each other.
> **Why it works:** You become the connector. Both people remember you as the one who made their best partnership happen. Triads compound — each introduction generates referrals, goodwill, and deal flow back to you.

---

## Step 1 — Set the Date and Load Environment

```
TODAY = current date (YYYY-MM-DD)
VAULT = /Users/Simon/Library/CloudStorage/GoogleDrive-severino@strategysprints.com/Shared drives/Team Sprints/TEAM Strategy Sprints/1 Operations/Obsidian Vault/SimVault26
PEOPLE_DIR = $VAULT/05 People
```

Read `~/.claude/.env` for environment variables (do NOT log or display secrets).

---

## Step 2 — Load the Network (Two Sources)

### 2a. Notion Partners Database (primary source)
- Database ID: `d054a72a98374b688549ca6a5454fdf5`
- Data source ID: `25a4b23f-602a-48ce-8ad3-d7a23da9164c`
- Search using `notion-search` with data_source_url `collection://25a4b23f-602a-48ce-8ad3-d7a23da9164c`
- Fetch each partner page to get: Name, Email, ICP, Superpower, Notes, Collab, Done JV, Next JV, Introduced To, Intro Date, Intro Status
- Partners with ICP and Superpower fields filled in are highest-quality matches
- **Duplicate prevention:** Check `Introduced To` field on every partner — if Person A's `Introduced To` already contains Person B's name, skip this pair

### 2b. Obsidian People Folder (enrichment)
Read all `.md` files in `$PEOPLE_DIR` (skip subfolders: `_Archive`, `_NoteCompanion`, `_Templates`, `Excalidraw`, `Granola*`, `⚡️Ideas`).

For each person file, extract:
- `name` (from frontmatter)
- `email` (from frontmatter)
- `company` (from frontmatter)
- `role` (from frontmatter)
- `tags` (from frontmatter)
- `relationship` (from frontmatter)
- **Expertise** section (bullet points)
- **Who They Are** section (paragraph)
- **Current Focus** section
- **Introduction Value** section (who they connect well with)

### 2c. Merge & Deduplicate
Merge both sources by name. If a person exists in both Notion Partners AND Obsidian, combine their data (Notion ICP/Superpower + Obsidian expertise/tags/Introduction Value).

**Filter out** people who:
- Have no email address
- Have `relationship: Active Client` (don't intro clients without explicit intent)
- Have empty Expertise AND empty "Who They Are" sections AND empty Superpower (not enough info to match)

---

## Step 3 — Enrich with Recent Signals

Gather fresh context in parallel:

### 3a. Gmail — Recent Conversations
Use `gmail_search_messages` with query: `newer_than:30d` to find people Simon has recently emailed. Cross-reference with the People list to identify who is "warm" right now.

### 3b. Calendar — Recent and Upcoming Meetings
Use `gcal_list_events` for the past 14 days and next 7 days. Extract attendee names. People Simon has recently met or is about to meet are prime triad candidates — the introduction feels natural ("I just spoke with [Name] and immediately thought of you").

### 3c. Introduction Value Links
Parse `## Introduction Value` sections for existing wikilinks (`[[Person Name]]`). These are pre-identified matches Simon has already flagged — prioritise these.

---

## Step 4 — Find the Best Triad Match

Score potential pairs using this priority system:

### Priority 1: Pre-Flagged Matches (Introduction Value section)
If Person A's "Introduction Value" mentions Person B (or vice versa), AND this pair has not been introduced before → this is the top pick.

### Priority 2: Same ICP, Adjacent Offers
Compare each pair's tags, expertise, ICP field, and Superpower:
- **Same ICP signal:** Overlapping tags, similar ICP fields, same type of client described
- **Adjacent offer signal:** Different Superpowers, different roles, different companies, non-competing services
- **Bonus:** Both are "warm" (recent email or calendar interaction)

### Priority 3: Warm + Complementary
If no strong ICP overlap found, match people who are both warm (recent contact) and have complementary skills that could lead to collaboration.

### Disqualify:
- Same company
- Already introduced (`Introduced To` field contains the other person's name)
- Both have identical offers (competitors, not adjacent)
- Either person has no email

Select the **single best pair** for today.

---

## Step 5 — Draft the Introduction Email

Create a Gmail draft using `gmail_create_draft`:

**To:** Both people's email addresses (comma-separated)
**Subject:** `Intro: [Person A First Name] ↔ [Person B First Name]`

**Body template:**

```
Hi [Person A First Name], hi [Person B First Name],

I want to connect you two — I think there's a natural fit.

[Person A First Name] — [one sentence: what Person B does and why it's relevant to Person A's world]

[Person B First Name] — [one sentence: what Person A does and why it's relevant to Person B's world]

You both [the shared ICP or shared context — e.g., "work with B2B SaaS founders" or "help agencies scale"]. Different angles, same client. That's usually where the best partnerships start.

I'll let you two take it from here.

Best,
Simon
```

**Rules for the draft:**
- Under 100 words
- No fluff, no over-explaining
- Specific about WHY these two should talk
- Reference the shared ideal client explicitly
- If there's a recent trigger (calendar, email), mention it: "I just spoke with [Name] yesterday and thought of you"
- Warm, direct, no formality

---

## Step 6 — Update Partners Database (Notion)

Update BOTH partner rows in the Partners database using `notion-update-page`:

For **Person A's** row:
| Property | Value |
|---|---|
| Introduced To | Person B's full name |
| Intro Date | Today's date |
| Intro Status | `Drafted` |

For **Person B's** row:
| Property | Value |
|---|---|
| Introduced To | Person A's full name |
| Intro Date | Today's date |
| Intro Status | `Drafted` |

If either person does not yet exist in the Partners database, create a new row using `notion-create-pages` with all available data (Name, Email, Superpower, ICP, Introduced To, Intro Date, Intro Status).

---

## Step 7 — Update Obsidian (Optional Enrichment)

If either person's file has an empty or `*TBD*` Introduction Value section, update it with the match:

```
## Introduction Value
- Connects well with: [[Person B]] (shared ICP: [description], adjacent offers)
```

This enriches the network graph for future triad matching.

---

## Step 8 — Report to Simon

Output a brief summary:

```
TRIAD — [TODAY]

Introducing: [Person A] ↔ [Person B]
Shared ICP: [who they both serve]
Adjacent offers: [Person A: X] + [Person B: Y]
Trigger: [why today — recent meeting, warm contact, pre-flagged]

Gmail draft created. Review and send before lunch.

Total introductions made: [count partners with non-empty Introduced To]
```

---

## Automation (launchd)

To run daily at 08:30 (before lunch, after /morning briefing):
```bash
# Create plist: ~/Library/LaunchAgents/com.strategysprints.triad.plist
# Schedule: Daily 08:30
# Command: /Users/Simon/.local/bin/claude -p "/triad"
# Logs: /tmp/triad.log
```
