# Entry Classification

## Work Domains → Categories

Based on user's work context (see [about.md](about.md)):

### Учёба
Подготовка к экзамену, аккредитации, собеседованию в частную клинику.

**Keywords:** урок, лекция, Anki, карточки, конспект, курс, тест, экзамен, аккредитация, собеседование, собес, частка, клиника, докма, АБТ, амбулаторная, терапия, ревматология

**→ Category:** task (p1-p2) → Todoist

### Блог
Посты в соцсетях для развития медицинского блога.

**Keywords:** пост, блог, контент, подписчики, TG, ВК, ОК, Threads, Instagram

**→ Category:** task (p3) → Todoist

### Консультации
Онлайн-консультации пациентов.

**Keywords:** консультация, пациент, приём, онлайн

**→ Category:** task (p4) → Todoist

### Здоровье
Тренировки, режим дня, физическая форма.

**Keywords:** зал, тренировка, отжимания, жим, масса, спорт

**→ Category:** task (p4) → Todoist

### Личное
Семья, отдых, отношения.

**Keywords:** родители, семья, мама, папа, отдых, кино, сериал

**→ Category:** task (p3-p4) → Todoist

---

## Decision Tree

```
Entry text contains...
│
├─ Экзамен/аккредитация/собес/частка/докма? ─────> TASK (p1)
│  (срочно, критично для карьеры)
│
├─ Урок/Anki/лекция/конспект/курс/тест? ─────────> TASK (p2)
│  (важно для подготовки к собеседованию)
│
├─ Пост/блог/контент? ───────────────────────────> TASK (p3)
│  (регулярная задача)
│
├─ Родители/семья? ──────────────────────────────> TASK (p3)
│  (важно для личной жизни)
│
├─ Консультация/пациент? ────────────────────────> TASK (p4)
│  (дополнительный доход)
│
├─ Зал/тренировка/отдых? ────────────────────────> TASK (p4)
│  (поддержание режима)
│
├─ Идея для блога/продукта? ─────────────────────> IDEA
│  (сохранить на потом)
│
├─ Осознание/инсайт? ────────────────────────────> REFLECTION
│  (личностный рост)
│
└─ Что-то узнал/выучил? ─────────────────────────> LEARNING
   (медицинские знания)
```

## Apply Decision Filters

Перед сохранением спроси:
- Поможет ли это сдать экзамен / аккредитацию / собеседование?
- Это срочно или может подождать до июля?
- Отвлечёт ли это от главной цели — устроиться в клинику?
- Могу ли я сказать этому "нет" до конца подготовки?

Если помогает цели → повысить приоритет.

---

## Photo Entries

For `[photo]` entries:

1. Analyze image content via vision
2. Determine domain:
   - Скриншот лекции/теста → Учёба
   - Статистика блога → Блог
   - Медицинский материал → Learning
3. Add description to daily file

---

## Output Locations

| Category | Destination | Priority |
|----------|-------------|----------|
| task (экзамен/собес) | Todoist | p1 |
| task (учёба) | Todoist | p2 |
| task (блог/родители) | Todoist | p3 |
| task (зал/консультации) | Todoist | p4 |
| idea | thoughts/ideas/ | — |
| reflection | thoughts/reflections/ | — |
| learning | thoughts/learnings/ | — |

---

## File Naming

```
thoughts/{category}/{YYYY-MM-DD}-short-title.md
```

Examples:
```
thoughts/ideas/2026-02-05-post-idea-therapy.md
thoughts/learnings/2026-02-05-abt-dosage.md
thoughts/reflections/2026-02-05-discipline-insight.md
```

---

## Thought Structure

Use preferred format:

```markdown
---
date: {YYYY-MM-DD}
type: {category}
domain: {Учёба|Блог|Консультации|Здоровье|Личное}
tags: [tag1, tag2]
---

## Context
[Что привело к мысли]

## Insight
[Ключевая идея]

## Implication
[Что это значит для подготовки к собеседованию / блога / жизни]

## Next Action
[Конкретный шаг — не абстрактный]
```

---

## Anti-Patterns (ИЗБЕГАТЬ)

При создании мыслей НЕ делать:
- Абстрактные рассуждения без Next Action
- Медицинская теория без применения к экзамену/практике
- Повторы без синтеза (кластеризуй похожие!)
- Хаотичные списки без приоритетов
- Задачи типа "подумать о..." (конкретизируй!)

---

## MOC Updates

After creating thought file, add link to:
```
MOC/MOC-{category}s.md
```

Group by domain when relevant:
```markdown
## Учёба
- [[2026-02-05-abt-dosage]] - Дозировки АБТ

## Блог
- [[2026-02-05-post-idea-therapy]] - Идея поста про терапию
```
