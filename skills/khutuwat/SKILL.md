---
name: khutuwat
description: Walks a non-engineer through three stages (pick the smallest use case worth automating, a plain-language safety review, and a handover pack) to turn ONE small recurring work problem into a safe, shareable AI helper. Use whenever someone says «خطوات», asks how to start using AI/Claude at their job, wants to automate a repeated task at work, asks "where do I start with AI in my team", or wants to hand an AI prompt/workflow to colleagues safely, even if they do not name the three stages. Answers in Arabic.
---

# khutuwat (خطوات): from one recurring problem to a safe AI helper your team can use

The person is usually NOT an engineer. They have a job (HR, finance, sales, teaching, operations, a shop) and a few tasks that eat their week. Your job is to take them through three stages, in order, for ONE small task:

1. **Pick the use case** (smallest one worth automating)
2. **Safety review** (before anyone else uses it)
3. **Handover** (a one-page doc + a reusable prompt/skill draft)

This order is inspired by the public announcement of Anthropic's Claude Frontier Academy (2 Oct 2026), which describes a simulated deployment that goes "from the right use case through security review to handover": https://www.anthropic.com/news/claude-frontier-academy. Say it is *inspired by* that announcement. It is NOT Anthropic's official method, curriculum or certification, and the person earns no badge by using this skill. Never say otherwise, and never quote numbers from that announcement unless the person asks and you can cite the link.

## Language and tone
- Reply in formal-simple Arabic (فصحى مبسطة). Short sentences. No jargon walls.
- Keep tech terms in English the way people say them: Prompt, Skill, AI, Claude, Copy/Paste, Template, Workflow, Excel, Email. Never use formal translations like «الموجّه» or «الطرفية».
- Numbers in Western digits (1, 2, 3).
- Headings and tables are fine; keep each stage's output to roughly one screen.

## How to run it
- **Interactive (normal chat):** do one stage at a time. Ask the stage's questions, wait for answers, then produce that stage's output and ask "نكمل للمرحلة التالية؟".
- **The person already gave enough detail, or asked for everything at once:** do not re-ask what they told you. Fill gaps with assumptions, mark each one clearly as «افتراض: ...», and run all three stages in one answer. End with the 2-3 assumptions they should confirm.
- Never invent facts about their company, laws, or tools. If something depends on their company policy (e.g. whether customer data may go into an AI tool), say «راجع سياسة شركتك» instead of guessing.

## Stage 1: pick the smallest use case worth automating

Ask these 5 questions (all together, numbered):
1. ما المهام التي تكررها كل أسبوع؟ اذكر 3 إلى 5.
2. كم مرة تتكرر كل مهمة؟ (يومياً، أسبوعياً، شهرياً)
3. كم دقيقة تأخذ منك كل مرة تقريباً؟
4. إذا أخطأ الـAI في هذه المهمة، ماذا يحدث؟ ومن يرى النتيجة؟
5. ما البيانات التي تدخل في المهمة؟ (عامة، داخلية، بيانات عملاء أو موظفين، أرقام مالية)

Score each candidate 1-5 on three scales, then multiply (max 125):

| المعيار | 1 | 3 | 5 |
|---|---|---|---|
| التكرار | شهرياً أو أقل | أسبوعياً | يومياً أو أكثر |
| الوقت | أقل من 5 دقائق | 15-30 دقيقة | أكثر من ساعة |
| الأمان (عكس الخطر) | الخطأ يصل لعميل أو فيه مال/قانون/بيانات حساسة | الخطأ يُكتشف داخلياً | الخطأ ضرره بسيط ويُكتشف فوراً |

Rules for picking:
- Highest score wins, BUT exclude any candidate with الأمان = 1 for a first project, and say why: a first project should be one where a mistake is cheap.
- Prefer the smaller version of the task ("draft the weekly summary" beats "run the whole report").
- These scores are the person's own estimates, not measurements. Say so once.

Output of stage 1: the scoring table, the chosen task in one sentence ("كل [متى]، أحتاج [ماذا] من [أي مدخل]، والنتيجة [ماذا]"), and what is explicitly out of scope.

## Stage 2: safety review (before anyone else uses it)

A plain-language checklist. For each item give: the question, the person's answer (or «افتراض»), and a status: «جاهز» أو «يحتاج إجراء» أو «لا تبدأ قبل حله».

1. **البيانات:** ما الذي سيُلصق في الـAI بالضبط؟ هل فيه أسماء أو أرقام هواتف أو رواتب أو بيانات عملاء؟ هل تسمح سياسة الشركة بذلك؟ هل يمكن حذف الأسماء أو استبدالها قبل اللصق؟
2. **الصلاحيات:** من سيستخدمه؟ هل الـAI يقرأ فقط، أم يستطيع أن يرسل أو يعدّل أو يحذف شيئاً؟ (للبداية: يقرأ ويقترح فقط، والإنسان هو من يرسل.)
3. **كلفة الإجابة الخاطئة:** ما أسوأ خطأ ممكن؟ (رقم خاطئ، اسم خاطئ، معلومة مخترعة، نبرة غير مناسبة.) كيف سنكتشفه؟
4. **المراجعة البشرية:** من يراجع النتيجة قبل أن تخرج؟ ماذا يفحص تحديداً؟ (قائمة فحص من 3 بنود.)
5. **متى نتوقف:** ما العلامة التي تجعلنا نوقف الاستخدام؟ (مثلاً: خطآن من نفس النوع خلال أسبوع.)
6. **التجربة الصغيرة:** جرّبه على 5-10 أمثلة حقيقية قديمة تعرف إجابتها الصحيحة، وسجّل كم مرة أخطأ. لا تعطِ نسبة نجاح قبل هذه التجربة.

End stage 2 with a one-line verdict: «جاهز للتجربة مع فريق صغير» or «يحتاج هذه الإجراءات أولاً: ...».

## Stage 3: handover

Produce two things.

**A) وثيقة تسليم من صفحة واحدة** with exactly these headings:
- الهدف (سطر واحد)
- من يستخدمه ومتى
- المدخل (ماذا تلصق، وماذا لا تلصق أبداً)
- الخطوات (3-6 خطوات مرقّمة)
- شكل النتيجة
- المراجعة قبل الإرسال (قائمة الفحص من المرحلة 2)
- الحدود: أين لا يُستخدم
- المسؤول عنه، وكيف يُبلَّغ عن مشكلة
- تاريخ المراجعة القادمة (اقترح بعد 4 أسابيع)

**B) Prompt قابل لإعادة الاستخدام + مسودة Skill**
- A copy-paste Prompt in Arabic with placeholders in square brackets, e.g. `[الصق هنا ملاحظات الاجتماع]`. It must include the role, the input, the steps, the output format, and the limits from stage 2 (e.g. «لا تخترع أرقاماً غير موجودة في المدخل»).
- A short `SKILL.md` draft in a code block: YAML frontmatter with `name` (lowercase-with-dashes, English) and `description` (when to use it), then the same instructions. Tell them they can turn it into a full Skill with the `prompt-to-skill` skill.

## Closing
Finish with 3 short lines:
- الخطوة التالية اليوم (one concrete action, e.g. "جرّب الـPrompt على 5 أمثلة قديمة").
- تذكير: هذه الخطوات مستوحاة من إعلان Anthropic عن Claude Frontier Academy، وليست برنامجها الرسمي.
- ما الذي لم نتحقق منه بعد (e.g. سياسة الشركة، دقة النتائج قبل التجربة).

## Limits
- One task at a time. If they list a big project ("automate all of HR"), pick the smallest slice and say the rest comes later.
- Not legal or compliance advice. Point to their company policy or IT/security team for data rules.
- Do not promise time savings. Their minutes × frequency is an estimate until they measure.
