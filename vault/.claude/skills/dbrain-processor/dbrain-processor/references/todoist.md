# Todoist Integration

## Available MCP Tools

### Reading Tasks
- `get-overview` — all projects with hierarchy
- `find-tasks` — search by text, project, section
- `find-tasks-by-date` — tasks by date range

### Writing Tasks
- `add-tasks` — create new tasks
- `complete-tasks` — mark as done
- `update-tasks` — modify existing

---

## Pre-Creation Checklist

### 1. Check Workload (REQUIRED)

```
find-tasks-by-date:
  startDate: "today"
  daysCount: 7
  limit: 50
```

Build workload map:
```
Пн: 2 tasks
Вт: 4 tasks  ← overloaded
Ср: 1 task   ← зал
Чт: 3 tasks  ← at limit
Пт: 2 tasks
Сб: 0 tasks  ← зал + буфер
Вс: 1 task
```

### 2. Check Duplicates (REQUIRED)

```
find-tasks:
  searchText: "key words from new task"
```

If similar exists → mark as duplicate, don't create.

---

## Priority by Domain

Based on user's work context (see [about.md](about.md)):

| Domain | Default Priority | Override |
|--------|-----------------|----------|
| Экзамен/Аккредитация/Собес | p1 | — |
| Учёба (уроки, Anki) | p2 | — |
| Блог (посты) | p3 | — |
| Родители/Семья | p3 | — |
| Консультации | p4 | — |
| Зал/Здоровье | p4 | — |
| Отдых | p4 | — |

### Priority Keywords

| Keywords in text | Priority |
|-----------------|----------|
| экзамен, аккредитация, собес, частка, докма, клиника, срочно | p1 |
| урок, Anki, лекция, конспект, карточки, курс, тест | p2 |
| пост, блог, родители, мама, папа | p3 |
| зал, консультация, отдых | p4 |

### Apply Decision Filters for Priority Boost

If entry matches goal filters → boost priority by 1 level:
- Поможет ли это сдать экзамен / аккредитацию / собеседование?
- Это срочно или может подождать до июля?

---

## Date Mapping

| Context | dueString |
|---------|-----------|
| **Экзамен/Собес deadline** | exact date |
| **Урок/Anki (ежедневно)** | today |
| **Пост (ежедневно)** | today |
| **На этой неделе** | friday |
| **На следующей неделе** | next monday |
| **Не указано** | in 3 days |

### Russian → dueString

| Russian | dueString |
|---------|-----------|
| сегодня | today |
| завтра | tomorrow |
| послезавтра | in 2 days |
| в понедельник | monday |
| в пятницу | friday |
| на этой неделе | friday |
| на следующей неделе | next monday |
| через неделю | in 7 days |
| 15 марта | March 15 |

---

## Task Creation

```
add-tasks:
  tasks:
    - content: "Task title"
      dueString: "friday"  # MANDATORY
      priority: "p4"       # based on domain
      projectId: "..."     # if known
```

### Task Title Style

User prefers: прямота, ясность, конкретика

✅ Good:
- "Законспектировать урок 45"
- "Перевести 3 урока в Anki"
- "Написать пост про терапию"
- "Позвонить маме"
- "Anki-повторение"

❌ Bad:
- "Подумать об учёбе"
- "Что-то с уроками"
- "Разобраться с Anki"

### Workload Balancing

If target day has 3+ tasks:
1. Find next day with < 3 tasks
2. Use that day instead
3. Mention in report: "сдвинуто на {day} (перегрузка)"

**Note:** Среда и суббота — дни зала, меньше учебных задач.

---

## Project Detection

Пока всё в Inbox (пользователь новичок в Todoist).

В будущем можно разделить:
| Keywords | Project |
|----------|---------|
| урок, Anki, лекция, экзамен, курс | Учёба |
| пост, блог, контент | Блог |
| консультация, пациент | Консультации |
| зал, тренировка | Здоровье |
| родители, семья, отдых | Личное |

If unclear → use Inbox (no projectId).

---

## Anti-Patterns (НЕ СОЗДАВАТЬ)

Based on user preferences:

- ❌ "Подумать о..." → конкретизируй действие
- ❌ "Разобраться с..." → что именно сделать?
- ❌ Абстрактные задачи без Next Action
- ❌ Дубликаты существующих задач
- ❌ Задачи без дат
- ❌ Задачи без учёта реального времени (1 карточка = 1 мин, 1 урок = 2-2.5 ч)

---

## Error Handling

CRITICAL: Никогда не предлагай "добавить вручную".

If `add-tasks` fails:
1. Include EXACT error message in report
2. Continue with next entry
3. Don't mark as processed
4. User will see error and can debug

WRONG output:
  "Не удалось добавить (MCP недоступен). Добавь вручную: Task title"

CORRECT output:
  "Ошибка создания задачи: [exact error from MCP tool]"
