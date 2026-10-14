---
name: prompt-to-skill
description: Beginner-friendly converter that turns a prompt someone keeps re-typing or copy-pasting into a proper Claude Skill folder (SKILL.md with name + description, rules, inputs, output format, limits, one example), then tests it once on one of their examples and reports what changed. Use whenever someone says «حوّل الـPrompt إلى Skill», "turn my prompt into a skill", "I paste the same prompt every day", "make this reusable", or shares a long saved prompt and wants it to run automatically. For coaching someone to design, test on 10+ inputs and improve a skill themselves, use skill-builder instead. Answers in Arabic.
---

# prompt-to-skill: your repeated Prompt becomes a Skill

Short beginner version. You do the writing; the person supplies the prompt and examples. If they want to learn to build and measure skills properly (10+ test inputs, defect rate, improvement loop), point them to the `skill-builder` skill from the same pack.

## Language
- Reply in formal-simple Arabic. Keep tech terms in English as people say them: Prompt, Skill, SKILL.md, frontmatter, Copy/Paste, Template, Claude, Claude Code.
- The SKILL.md you write: frontmatter `name` in lowercase English with dashes; `description` in English (it triggers more reliably) and mention the Arabic words the person uses for the task; body instructions in English; tell the skill to answer in the language the person's prompt uses (Arabic if the prompt is Arabic).

## Step 1: collect (ask once, all together)
1. الصق الـPrompt الذي تكرره كما هو.
2. أعطني مثالين لنتيجة جيدة (ما أعطاك Claude وأعجبك، أو ما كتبته أنت بيدك). ومع كل مثال: ماذا كان المدخل؟
3. متى تستخدمه عادة؟ (ما الجملة التي تكتبها أو الموقف)
4. هل هناك شيء يجب ألا يفعله أبداً؟

If they already gave some of this, do not re-ask it. If they have only one example or none, continue but mark the gap: «افتراض: ...» and note that the test in step 4 will be weaker.

## Step 2: extract (show this table before writing)
| الجزء | ما وجدته في الـPrompt والأمثلة |
|---|---|
| المهمة | one sentence |
| المدخلات | what the user pastes or attaches each time; which parts change each time (these become placeholders/questions) |
| القواعد | rules stated in the prompt, plus rules visible only in the good examples (length, tone, structure, what is always included) |
| شكل النتيجة | headings, order, length, format |
| الحدود | what it must not do / invent |
| متى يُستخدم | trigger phrases for the description |

Rules hidden in the examples matter most: if both examples start with a one-line summary, that is a rule even if the prompt never said it. Say which rules came from the examples.

## Step 3: write the Skill folder
If you can write files (e.g. Claude Code), create:
```
<skill-name>/
├── SKILL.md
└── examples/
    └── example-1.md   (input + good output from the person, unchanged)
```
If you cannot write files (e.g. Claude.ai chat), print each file in its own code block with its path as a title, and tell them how to save and zip it (folder name = skill name; SKILL.md inside the folder).

SKILL.md template (keep it under ~100 lines):
```markdown
---
name: <lowercase-with-dashes>
description: <What it does in one sentence>. Use when <situations and phrases, including the Arabic words they use>. <Language it answers in>.
---

# <Title>

## What you receive
## Steps
1. ...
## Output format
## Rules
## Limits (when not to use it, what never to invent)
## Example
See examples/example-1.md
```
Write the description "pushy" enough to trigger: list the real situations and phrases, not just a label.

## Step 4: test once, then report
- Take the input of ONE of their examples (prefer the second; keep the first as the reference style). Follow the new SKILL.md exactly as written, as if you had never seen the original prompt, and produce the output. Show that output in your reply so the person can judge it.
- If their examples have no full input (only the output), write a short sample input yourself, say clearly that the test used your sample and not their real data, and ask them to rerun it on one real input.
- Compare with their good output on: structure, length, rules followed, anything invented.
- If a difference comes from an unclear instruction, fix the SKILL.md (one change per problem) and say what you changed.

Report in Arabic, in this shape:
- **ما أنشأته:** list of files.
- **نتيجة التجربة (n=1):** what matched, what did not.
- **ما غيّرته بعد التجربة:** each change in one line, or «لا شيء».
- **اقتراحات لم أضفها:** rules you think are missing but did not add, or «لا شيء».
- **تنبيه:** تجربة واحدة فحص سريع، وليست دليلاً على الجودة. جرّبه على 10 أمثلة حقيقية قبل أن تعتمد عليه أو تشاركه (و`skill-builder` يساعدك في ذلك).
- **كيف تضيفه:** Claude.ai: ارفع الملف المضغوط (zip) من Customize ← Skills. Claude Code: انسخ المجلد إلى `~/.claude/skills/`.

## Limits
- Do not add rules, facts or steps that are not in the prompt or the examples. If something seems missing (e.g. what to do when the input is too short), list it in the report under «اقتراحات لم أضفها» instead of silently adding it.
- Never put passwords, API keys, or personal data from the examples into the skill files; replace them with placeholders and say so.
- One prompt becomes one skill. If the prompt does several unrelated jobs, suggest splitting it.
