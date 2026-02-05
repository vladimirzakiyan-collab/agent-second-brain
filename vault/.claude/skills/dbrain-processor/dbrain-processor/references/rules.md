# Critical Processing Rules

See [about.md](about.md) for user context and preferences.

## Rule 1: Skip Processed Entries

```
If entry contains `<!-- ✓ processed` → SKIP COMPLETELY
```

Check AFTER each `## HH:MM` header for the marker.

## Rule 2: Every Task = Date

**NEVER create a task without `dueString`:**

| Text | dueString |
|------|-----------|
| завтра | tomorrow |
| в пятницу | friday |
| на этой неделе | friday |
| в четверг | thursday |
| 15 марта | March 15 |
| NOT SPECIFIED | in 3 days |

## Rule 3: Check Duplicates

**BEFORE creating any task:**

1. Call `find-tasks` with key words from task
2. If similar task exists → **DO NOT CREATE**
3. Mark as: `<!-- ✓ processed: task (duplicate) -->`

## Rule 4: Consider Workload

**BEFORE creating tasks:**

1. Call `find-tasks-by-date` with `startDate: "today"`, `daysCount: 7`
2. Count tasks per day
3. If target day has 3+ tasks → shift to next day with less load
4. **Note:** Среда и суббота — дни зала, меньше учебных задач

## Rule 5: Mark After Processing

After EACH processed entry, add marker:

```markdown
<!-- ✓ processed: {category} -->
```

For tasks with details:
```markdown
<!-- ✓ processed: task → Todoist: {name} {priority} {date} -->
```

## Rule 6: Apply Decision Filters

Before saving any thought or task, check:
- Поможет ли это сдать экзамен / аккредитацию / собеседование?
- Это срочно или может подождать до июля?
- Отвлечёт ли это от главной цели — устроиться в клинику?
- Могу ли я сказать этому "нет" до конца подготовки?

If helps goal → boost priority.

## Rule 7: Respect Time Calculations

**CRITICAL for this user:**

- 1 карточка Anki (повторение) = 1 минута
- 1 старый урок → Anki = 30 минут
- 1 новый урок (полный цикл) = 120–150 минут
- 100–300 карточек с урока

Don't create unrealistic plans!

## Rule 8: Avoid Anti-Patterns

NEVER create:
- Абстрактные задачи без Next Action ("Подумать о...")
- Хаотичные списки без приоритетов
- Повторы без синтеза
- Задачи без учёта реального времени
- Кино/сериалы/игры до выполнения дневного плана

See [about.md](about.md) → Anti-Patterns section.

---

## Checklist Before Completion

- [ ] All new entries processed
- [ ] No duplicates in Todoist
- [ ] All tasks have dates and concrete actions
- [ ] Decision filters applied
- [ ] Time calculations respected
- [ ] Anti-patterns avoided
- [ ] MOC files updated
- [ ] Report generated
