# Wiki-Links Building

## Purpose

Build connections between notes to create a knowledge graph.

## When Saving a Thought

### Step 1: Search for Related Notes

Search thoughts/ for related content:

```
Grep "keyword1" in thoughts/**/*.md
Grep "keyword2" in thoughts/**/*.md
```

Keywords to search:
- Main topic of the thought
- Key entities (medications, conditions, techniques)
- Domain terms (терапия, АБТ, ревматология)

### Step 2: Check MOC Indexes

Read relevant MOC files:

```
MOC/
├── MOC-ideas.md
├── MOC-learnings.md
└── MOC-reflections.md
```

Find related entries.

### Step 3: Link to Goals

Check if thought relates to goals:

```
Read goals/1-yearly-2026.md
Find matching goal areas
```

### Step 4: Add Links to Note

In the thought file, add:

**In frontmatter:**
```yaml
related:
  - "[[thoughts/learnings/2026-02-05-abt-dosage.md]]"
  - "[[goals/1-yearly-2026#Career & Business]]"
```

**In content (inline):**
```markdown
This connects to [[АБТ дозировки]] we learned earlier.
```

**In Related section:**
```markdown
## Related
- [[Previous related thought]]
- [[Goal this supports]]
```

### Step 5: Update MOC Index

Add new note to appropriate MOC:

```markdown
# MOC: Learnings

## Recent
- [[thoughts/learnings/2026-02-05-new-learning.md]] — Brief description

## By Topic
### Терапия
- [[thoughts/learnings/2026-02-05-abt-dosage.md]]

### Ревматология
- [[thoughts/learnings/2026-02-05-ra-treatment.md]]
```

### Step 6: Add Backlinks

In related notes, add backlink to new note if highly relevant.

## Link Format

### Internal Links
```markdown
[[Note Name]]                    # Simple link
[[Note Name|Display Text]]       # With alias
[[folder/Note Name]]             # With path
[[Note Name#Section]]            # To heading
```

### Link to Goals
```markdown
[[goals/1-yearly-2026#Career & Business]]
[[goals/3-weekly]] — ONE Big Thing
```

## Report Section

Track new links created:

```
<b>🔗 Новые связи:</b>
• [[Note A]] ↔ [[Note B]]
• [[New Thought]] → [[Related Learning]]
```

## Example Workflow

New thought: "Узнал про новую схему АБТ при пневмонии"

1. **Search:**
   - Grep "АБТ" in thoughts/ → finds related notes
   - Grep "пневмония" in thoughts/ → no results

2. **Check MOC:**
   - MOC-learnings.md has "Терапия" section

3. **Goals:**
   - 1-yearly-2026.md has "Устроиться в частную клинику" goal

4. **Create links:**
   ```yaml
   related:
     - "[[thoughts/learnings/2026-01-15-abt-basics.md]]"
     - "[[goals/1-yearly-2026#Career & Business]]"
   ```

5. **Update MOC-learnings.md:**
   ```markdown
   ### Терапия
   - [[thoughts/learnings/2026-02-05-abt-pneumonia.md]] — Схема АБТ при пневмонии
   ```

6. **Report:**
   ```
   <b>🔗 Новые связи:</b>
   • [[АБТ при пневмонии]] ↔ [[Основы АБТ]]
   ```

## Orphan Detection

A note is "orphan" if:
- No incoming links from other notes
- No related notes in frontmatter
- Not listed in any MOC

Flag orphans for review:
```
<b>⚠️ Изолированные заметки:</b>
• [[thoughts/ideas/orphan-note.md]]
```
