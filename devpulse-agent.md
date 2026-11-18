# DEV PULSE – DAILY CODE REFRESHER

Internal notes. This file is not published on the site. The automation checks out this repository and follows this file. It posts one Slack message. It does not send email, and it does not edit the repo.

DevPulse is a technical refresher for someone who reviews architecture and code more often than they write it. Each message covers JavaScript, SQL, PHP, and Python. Write structured study notes in fluent English: state the central theme, explain each topic under consistent labels, show one useful example, and finish with practical takeaways. The length of each section follows that topic.

Use the calendar date in Europe/London. One message per date, including Saturday and Sunday. A second run on the same date does not post again.

## WHICH LESSONS

One message contains four lessons, one from each list below, in this order: JavaScript, SQL, PHP, Python.

A topic is one lesson when one sitting covers it. It is two or more lessons only when the next part is a different mechanism. Do not stretch a topic to fill a week, and do not compress two mechanisms into one lesson because a list is short.

Count whole days from 2026-01-01 to the Europe/London date. That count is 0 on 2026-01-01. For each list, the lesson number is `(that count modulo the number of lessons in that list) + 1`. Use those four lessons. Do not pick different topics.

Index each list on its own. A lesson's number in one list has nothing to do with the number in another.

### JavaScript

Five lessons.

1. Hoisting, the temporal dead zone for `let` and `const`, and coercion (`==` against `===`).
2. `map`, `reduce`, and `flatMap` against a loop, with the time and space cost.
3. A closure, and a default parameter when it changes what the function remembers.
4. The module pattern, and what stays private. The closure lesson has already covered how a function keeps a variable. This lesson is only the module.
5. The event loop, and a microtask against a macrotask.

### SQL

Six lessons.

1. Implicit casts in `WHERE`, and how a cast stops an index being used.
2. A correlated subquery against a `JOIN`, and what the plan is doing.
3. An expression in `SELECT` against one in `WHERE`, and a deterministic function.
4. Normalisation against a deliberate denormalised read.
5. Locking, and what a second writer waits on.
6. Isolation levels, and which anomalies each one still allows. Locking was the previous lesson. This lesson is what a reader is allowed to see.

### PHP

Five lessons.

1. `declare(strict_types=1)`, `==` against `===`, and how scalars are copied.
2. `yield`, and reading a large set without holding it all.
3. Local scope, and passing a value against passing a reference.
4. The strategy pattern with an interface and dependency injection.
5. One request, no shared memory with the next, and a race on a file.

### Python

Seven lessons.

1. A mutable default argument.
2. `global` against `nonlocal`.
3. A comprehension against a generator, and what each keeps in memory.
4. LEGB and a closure.
5. A context manager (`__enter__` and `__exit__`).
6. The GIL.
7. Threads against processes against `asyncio`. The GIL lesson has already said what the lock is. This lesson is which tool to use.

## EACH LESSON

Every section of the message has these parts, in this order:

1. **Numbered heading.** `1. JavaScript — topic`, then SQL, PHP, and Python as sections 2–4.
2. **Key lesson.** One bold sentence stating the mental model to remember. It must say more than the topic name.
3. **Explanation.** Short paragraphs or bullets that define the important terms and explain what the runtime or database actually does. Prefer one idea per bullet. Use complete sentences rather than fragments.
4. **Example.** Introduce one realistic snippet with `Example:`. Fence it with `javascript`, `sql`, `php`, or `python` so Slack colour-codes it. Add a second snippet only when it is needed to show the safe form.
5. **Why it behaves that way.** Explain the result, including evaluation order, scope, conversion, memory, concurrency, or query-plan behaviour as appropriate.
6. **Best practice.** Finish with two to four concrete actions under `Best practice:`. Include a fix for a gotcha. Include time and space cost here when it matters.

The explanation may mix compact paragraphs and bullets. It should read like clear revision notes, not a wall of prose and not a list of unexplained definitions. A reader returning to the topic after several months should understand both the rule and the reason.

Use precise language. Distinguish what syntax appears to say from what the runtime or database does. When behaviour differs by database engine, language version, runtime, or build, name the environment. Do not present an engine-specific example as universal.

For version-sensitive claims, verify them against current official documentation available to the run. If that cannot be done, explain the stable principle and omit the exact version claim. Do not rely on memory for release numbers.

Write as much as the mechanism needs, then stop. Do not teach unrelated boilerplate or add a second topic.

## THE SLACK MESSAGE

Post one message with this structure:

1. `[DevPulse Daily]`
2. `Summary`
3. Two or three sentences identifying the central theme shared by the day's four lessons.
4. `The refresher covers four areas.`
5. Four numbered sections in the order JavaScript, SQL, PHP, Python, each using the lesson structure above.
6. `Key takeaways for a software engineer` followed by one concise bullet per language.
7. `What to prioritise learning` followed by three to five broader concepts drawn from the four lessons.
8. One final sentence stating the overarching lesson.

Every code block is fenced with its language on the opening line (`javascript`, `sql`, `php`, or `python`). Match the length of each section to the topic. The closing synthesis must draw together the day's lessons rather than introduce new material.

This is the shape of the daily message, not the lessons for today. Do not post this sample. Look up the four lessons for the date. A larger topic is longer than a section below.

~~~~
[DevPulse Daily]

Summary

The central theme is that code can behave differently from what its surface syntax suggests. Understanding when values are created, converted, evaluated, and shared helps prevent subtle bugs.

The refresher covers four areas.

1. JavaScript — equality and coercion

**Key lesson: `==` may convert values before comparing them, while `===` compares type and value.**

- Loose equality asks whether values become equal after JavaScript's coercion rules.
- Strict equality does not convert one operand to the other's type.

Example:

```javascript
"0" == false;  // true
"0" === false; // false
```

The first comparison converts the operands according to the loose-equality algorithm. The second sees a string and a boolean, so it is false.

Best practice:

- Prefer `===`.
- Convert intentionally with `Number`, `String`, or `Boolean` when input crosses a boundary.

2. SQL — `SELECT` against `WHERE`

**Key lesson: filtering and output expressions occur at different logical stages of a query.**

`WHERE` decides which rows survive before the `SELECT` list produces output values. A `SELECT` alias therefore is not generally available to `WHERE`, although it is generally available to `ORDER BY`.

Example:

```sql
SELECT total * tax_rate AS tax
FROM invoices
WHERE total > 100;
```

Best practice:

- Use a subquery or CTE when a calculated value must be filtered.
- Name the database engine when discussing non-deterministic functions or optimiser behaviour.

3. PHP — strict types

**Key lesson: scalar argument coercion depends on the file making the call.**

Explain the selected PHP lesson here, then show a fenced PHP example and its best practices.

4. Python — shared state

**Key lesson: protecting shared state and running CPU work in parallel are different problems.**

Explain the selected Python lesson here, then show a fenced Python example and its best practices.

Key takeaways for a software engineer

- JavaScript: Prefer explicit conversion and strict equality.
- SQL: Know which query stage evaluates each expression.
- PHP: Type declarations do not remove every coercion boundary.
- Python: Choose concurrency tools according to the work and protect shared state.

What to prioritise learning

- Execution and evaluation order.
- Type conversion at system boundaries.
- Database plans and engine-specific behaviour.
- Concurrency, parallelism, and shared state.

The overarching lesson is to understand what the runtime or database does, not only what a line of code appears to say.
~~~~

## DO NOT

- Skip Saturday or Sunday.
- Post a second message on the same date.
- Post the four lessons as four messages.
- Drop a language.
- Send email.
- Edit this repository.
- Invent a topic that is not that language's lesson for the date.
- Add a second topic inside a section.
- Pad a small topic, or cut a topic short to fit a fixed length.
- Write bullets that name terms without explaining what the runtime or database does.
- Present engine-specific or version-specific behaviour as universal.
- State a release number or recent language change without checking current official documentation.
- Post a code block with no language tag.
- Quote a price or mention a prospect.

## THE SAVED PROMPT

This section is for the person setting the automation. The run follows the sections above.

```
Check out this repository and follow docs/devpulse-agent.md on that checkout. That file is the brief. Do not wait for it to be pasted.

Follow the schedule set on this automation. Use the Europe/London date, including Saturday and Sunday. Post one Slack message for that date. Start with a short summary of the shared theme. Then write four numbered lessons—JavaScript, SQL, PHP, and Python—taken from the lists in that file. Each lesson has a bold key lesson, a clear explanation, a fenced example, why it behaves that way, and practical best practices. End with language-by-language takeaways, three to five learning priorities, and one overarching lesson. Name the database engine, runtime, version, or build when behaviour differs, and verify version-sensitive claims against current official documentation. Fence every snippet with javascript, sql, php, or python so Slack colour-codes it. Do not send email. Do not edit the repository.
```
