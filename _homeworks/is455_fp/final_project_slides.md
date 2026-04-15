---
layout: slides
title: The Audacity of Scope
subtitle: Final Project for IS 455
instructor: Lamis Alghamdi
#course: IS455 Database Design & Prototyping
#semester: Spring 2026
---

## Heading Levels

### This is an h3 heading

#### This is an h4 heading (muted style)

Regular paragraph text lives here. It uses the base font at normal weight with comfortable line-height for readability on projected slides.

**Bold text** stands out, and [links look like this](https://example.com).

---

## Unordered Lists

- First item in the list
- Second item with more detail
- Third item
  - Nested item underneath
  - Another nested item
- Back to the top level

---

## Ordered Lists

1. Download and install the required tools
2. Clone the repository to your local machine
3. Run the setup script
4. Verify everything works
   1. Check the database connection
   2. Check the API endpoints

---

## Code

Inline code looks like this: `SELECT * FROM users;`

Code blocks get their own styled container:

```sql
CREATE TABLE projects (
    id          SERIAL PRIMARY KEY,
    title       VARCHAR(255) NOT NULL,
    description TEXT,
    created_at  TIMESTAMP DEFAULT NOW()
);

SELECT p.title, COUNT(t.id) AS task_count
FROM projects p
LEFT JOIN tasks t ON t.project_id = p.id
GROUP BY p.title
ORDER BY task_count DESC;
```

---

## Tables

| Feature       | Status    | Priority |
|---------------|-----------|----------|
| User auth     | Done      | High     |
| Dashboard     | In progress | High   |
| Export to CSV | Planned   | Medium   |
| Dark mode     | Planned   | Low      |

---

## Blockquotes

> Good design is as little design as possible. Less, but better — because it concentrates on the essential aspects, and the products are not burdened with non-essentials.

Regular text continues after the blockquote without interruption.

---

## Text Size Utilities

Regular paragraph text at base size.

<p class="mediumtext">Medium text — slightly smaller, useful for secondary information or captions.</p>

<p class="smalltext">Small text — for footnotes, attributions, or fine print that shouldn't dominate the slide.</p>

<p class="tinytext">Tiny text — for source citations or legal disclaimers at the very bottom.</p>

---

## Two-Column Layout (left/right)

<div class="left">

**Left Column**

- Database schema
- ER diagrams
- Normalization rules

</div>

<div class="right">

**Right Column**

- Query optimization
- Index strategies
- Performance tuning

</div>

---

## Two-Column Layout (multiCol)

<div class="multiCol">
<div class="col">

**Relational Databases**

PostgreSQL, MySQL, SQLite — structured data, ACID compliance, mature tooling.

</div>
<div class="col">

**Document Stores**

MongoDB, CouchDB — flexible schemas, JSON-native, horizontal scaling.

</div>
</div>

---

## Fragments (Step Reveal)

Press → to reveal each point:

- First, we define the problem <!-- .element: class="fragment" -->
- Then, we gather the data <!-- .element: class="fragment" -->
- Next, we build the prototype <!-- .element: class="fragment" -->
- Finally, we test and iterate <!-- .element: class="fragment" -->

---

## Step Fade In/Out Fragments

<span class="fragment step-fade-in-then-out">Step 1: Requirements gathering</span>
<span class="fragment step-fade-in-then-out">Step 2: Schema design</span>
<span class="fragment step-fade-in-then-out">Step 3: Implementation</span>
<span class="fragment step-fade-in-then-out">Step 4: Deployment</span>

Each step replaces the previous one.

---

## Images

Images are auto-centered with no border or shadow:

![Placeholder](https://via.placeholder.com/600x250/f8f9fa/6b7280?text=Your+Image+Here)

---

## Centered Text

<div class="centered">

### This heading is centered

So is this paragraph. Use the `centered` class on a wrapping div.

</div>

---

## Big Text

<div class="centered">
<bigtext>42</bigtext>

The answer to everything.

</div>

---

## Mixed Content Slide

### Project Timeline

| Phase     | Weeks | Deliverable         |
|-----------|-------|---------------------|
| Research  | 1–2   | Literature review    |
| Design    | 3–4   | ER diagram + schema  |
| Build     | 5–8   | Working prototype    |
| Test      | 9–10  | Test results report  |

> Start early. The build phase always takes longer than you think.

---

## Vertical Slides

Use `----` in your markdown to create vertical (nested) slides.

Press ↓ to go down.

----

### Vertical Slide 1

This is a sub-slide underneath the parent.

----

### Vertical Slide 2

Another sub-slide. Press ← to go back up and continue.

---

## Speaker Notes

This slide has speaker notes — press `S` to open the speaker view.

Notes are invisible to the audience.

note:
These are speaker notes. Only visible in speaker view.
Remind students about the final project deadline.
Mention office hours on Thursday.

---

## Math (LaTeX)

Inline math: $E = mc^2$

Block math:

`$$\sum_{i=1}^{n} x_i = x_1 + x_2 + \cdots + x_n$$`

---

## That's It

All style features demonstrated:

headings, paragraphs, bold, links, unordered lists, ordered lists, nested lists, inline code, code blocks, tables, blockquotes, text sizes (medium/small/tiny), left/right columns, multiCol columns, fragments, step-fade fragments, images, centered text, bigtext, vertical slides, speaker notes, and math.

