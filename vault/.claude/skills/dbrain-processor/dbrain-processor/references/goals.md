# Goals Integration

## ALWAYS Do First

Before processing daily entries:

1. **Read current focus:**
   ```
   Read goals/3-weekly.md → Extract ONE Big Thing
   ```

2. **Read yearly goals:**
   ```
   Read goals/1-yearly-2026.md → Know active goals by area
   ```

3. **Check monthly priorities:**
   ```
   Read goals/2-monthly.md → Top 3 priorities
   ```

## Goal Alignment

When creating a task, ask:

1. **Does it connect to ONE Big Thing?**
   - Yes → add to task description: `→ Weekly focus`
   - No → continue checking

2. **Does it connect to monthly priority?**
   - Yes → add: `→ Monthly: [Priority name]`
   - No → continue checking

3. **Does it connect to yearly goal?**
   - Yes → add: `→ Goal: [Goal name]`
   - No → mark as "operational"

## Task Priority Boost

If task aligns with goals, consider priority bump:

| Alignment | Default | Boost to |
|-----------|---------|----------|
| ONE Big Thing | p3 | p2 |
| Monthly priority | p3 | p2-p3 |
| Yearly goal | p4 | p3 |
| No alignment | p4 | p4 |

## Current Goals (February 2026)

### ONE Big Thing (Weekly)
Закрыть отставание по урокам — 6 уроков → 0.

### Monthly Top 3
1. Закрыть отставание и догнать курс
2. Anki без пропусков (с 5 февраля)
3. Посты каждый день

### Yearly Goals
1. Устроиться в частную клинику (собес 1 июля)
2. Поступить в ординатуру по ревматологии
3. Закончить курсы АБТ и амбулаторной
4. 10к–50к подписчиков в ТГ
5. Жим лёжа 100 кг
6. Найти партнёра-армянку
7. Выработать самодисциплину
8. Доход 200–300к/мес

## Saving Thoughts

When saving to thoughts/:

1. **Check goal relevance:**
   - Scan goals/1-yearly-2026.md for matching areas
   - If matches → add link in frontmatter:
     ```yaml
     related:
       - "[[goals/1-yearly-2026#Career & Business]]"
     ```

2. **Tag with goal area:**
   ```
   #goal/career
   #goal/health
   #goal/learning
   #goal/blog
   ```

## Goal Progress Tracking

Track goal activity by:

- Task created → goal is "active"
- Thought saved → goal is "active"
- No activity 7+ days → "stale"
- No activity 14+ days → "warning"

## Report Section

Add to report:

```
<b>📈 Прогресс по целям:</b>
{for each active yearly goal with recent activity:}
• {goal}: {progress}% {status_emoji}

{if stale goals:}
<b>⚠️ Требует внимания:</b>
• Цель "{goal}" без активности {days} дней
```

## Goal File Parsing

### 3-weekly.md — Find ONE Big Thing

Look for pattern:
```markdown
> **If I accomplish nothing else, I will:**
> [THE ONE THING]
```

### 1-yearly-2026.md — Find Active Goals

Look for tables:
```markdown
| Goal | Progress | Status |
|------|----------|--------|
| Goal name | X% | 🟡 |
```

### 2-monthly.md — Find Top 3

Look for section:
```markdown
## Top 3 Priorities

### Priority 1: [Priority 1]
### Priority 2: [Priority 2]
### Priority 3: [Priority 3]
```

## Example Alignment

Entry: "Нужно законспектировать урок 46"

Check:
- ONE Big Thing: "Закрыть отставание по урокам" → ✅ Related
- Monthly #1: "Закрыть отставание и догнать курс" → ✅ Related
- Yearly: "Устроиться в частную клинику" → ✅ Related

Result:
```
Task: Законспектировать урок 46
Description: → Weekly focus → Monthly: Догнать курс → Goal: Частная клиника
Priority: p2 (aligned with ONE Big Thing)
```
