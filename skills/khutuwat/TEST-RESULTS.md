# TEST-RESULTS: khutuwat

**Date:** 2026-10-12 · **Kind:** smoke test, not proof. Each run is n=1. Total runs: 2, on two different inputs. No defect rate is claimed.

**How:** the skill folder was copied to `<tmp>/.claude/skills/khutuwat/` and run with `claude -p "<prompt>" --permission-mode acceptEdits --allowedTools "Skill WebFetch Read Write Edit Glob" --output-format stream-json --verbose`. The transcript shows whether the `Skill` tool was called.

## Summary
| Run | Input | Skill triggered | Result |
|---|---|---|---|
| 1 | Accountant, 3 tasks, "all stages at once" | yes | All 3 stages in one answer. The 2 money/customer tasks were excluded (safety = 1) and the weekly expense report was picked (score 45). Assumptions were marked, the 6-item checklist had statuses, and it produced the handover doc, Prompt and SKILL.md draft. The "inspired by, not official" line was present. |
| 2 | Only the keyword «خطوات» | yes | Asked the 5 questions, explained the scoring, and said "inspired by, not official, no certificate". It waited for answers as intended. |

**What worked:** triggering on the bare keyword; formal-simple Arabic with English tech terms; no invented numbers (the scores came from the user's own minutes); the disclaimer.
**What failed or is unverified:** nothing broke in these 2 runs. Not yet tested: a multi-turn conversation (stage by stage), Claude.ai (only Claude Code was tested), other models (the runs used `claude-sonnet-5-5`), and vague or very large inputs ("automate all of HR").
**Changes after testing:** none to this skill. Emoji status markers were replaced with words before the first run.

## Run 1: accountant, all stages at once

- Model: `claude-sonnet-5-5` (Claude Code 2.1.296 default for `claude -p`), skill listed at startup: yes
- Tools called, in order: Skill
- Duration: 34s, error: False

**Prompt:**

```text
خطوات. أشتغل محاسب بمكتب صغير (6 موظفين). كل يوم أطابق كشف البنك ويا الفواتير بالإكسل (تقريباً 45 دقيقة)، كل أسبوع أكتب تقرير مصاريف للمدير (ساعة ونص)، وكل شهر أرسل تذكير للعملاء المتأخرين بالدفع (20 عميل، كل إيميل 5 دقايق). أريد أبدي بالـAI بس ما أعرف منين. اعطني المراحل كلها مرة وحدة.
```

**Final output (verbatim):**

````markdown
# خطوات: من مهمة متكررة إلى مساعد AI آمن

أعطيتني ما يكفي، فسأشغّل المراحل الثلاث معاً. الافتراضات مكتوبة بوضوح، وفي آخر الرد أسئلة تؤكدها.

---

## المرحلة 1: اختيار أصغر مهمة تستحق الأتمتة

الدرجات من 1 إلى 5 لكل معيار، والنتيجة حاصل الضرب (الحد الأقصى 125). هي تقديراتي من كلامك، وليست قياسات.

| المهمة | التكرار | الوقت | الأمان | الناتج |
|---|---|---|---|---|
| مطابقة كشف البنك مع الفواتير | 5 (يومياً) | 4 (45 دقيقة) | 1 (أرقام مالية، وخطأ قد يمر دون أن يُلاحظ) | 20، مستبعدة |
| تقرير المصاريف الأسبوعي للمدير | 3 (أسبوعياً) | 5 (ساعة ونصف) | 3 (يُكتشف داخلياً قبل وصوله للمدير) | **45** |
| تذكير العملاء المتأخرين | 1 (شهرياً) | 5 (100 دقيقة) | 1 (الإيميل يصل للعميل ويتعلق بالمال) | 5، مستبعدة |

**المهمة المختارة:**
> كل أسبوع، أحتاج مسودة نص تقرير المصاريف (ملخص وملاحظات وبنود لافتة) من جدول الأرقام الذي أجهزه في Excel، والنتيجة مسودة أراجعها قبل إرسالها للمدير.

**افتراض:** الأرقام تبقى من حسابك أنت في Excel. الـAI يكتب الشرح والملخص فقط ولا يحسب بدلاً منك.

**خارج النطاق الآن:**
- مطابقة البنك: مال ويومي، وخطؤها مكلف. يمكن العودة إليها لاحقاً بشكل أصغر، مثل اقتراح أسباب الفروقات فقط.
- إيميلات التذكير: تصل للعملاء. يمكن لاحقاً أن يكتب الـAI قالباً واحداً فقط وأنت من يرسل.

---

## المرحلة 2: مراجعة الأمان

| البند | الإجابة | الحالة |
|---|---|---|
| **البيانات** | افتراض: تلصق جدول مصاريف مجمّعاً حسب البند، بلا أسماء موردين أو عملاء أو موظفين. | يحتاج إجراء: راجع سياسة شركتك عن إدخال الأرقام المالية في أدوات AI. |
| **الصلاحيات** | يقرأ ويقترح فقط. لا يرسل ولا يعدّل ملفاً. أنت من تنسخ وترسل. | جاهز |
| **كلفة الخطأ** | أسوأ خطأ: رقم مخترع أو نسبة محسوبة خطأ في ملخص يقرؤه المدير. | يحتاج إجراء: قاعدة «كل رقم في النص يجب أن يكون في الجدول». |
| **المراجعة البشرية** | أنت. قائمة الفحص: (1) كل رقم في النص موجود في جدولك. (2) النسب والمقارنات صحيحة. (3) لا اسم ولا معلومة لم تُدخلها. | جاهز |
| **متى نتوقف** | خطآن رقميان من نفس النوع خلال أسبوع، أو أي معلومة مخترعة. | جاهز |
| **التجربة الصغيرة** | جرّبه على 5 تقارير قديمة تعرف أرقامها، وسجّل كم رقماً أو جملة خاطئة ظهرت. لا نسبة نجاح قبل ذلك. | يحتاج إجراء |

**الحكم:** يحتاج هذه الإجراءات أولاً: التأكد من سياسة الشركة عن الأرقام المالية، وتجربة الـPrompt على 5 تقارير قديمة.

---

## المرحلة 3: التسليم

### أ) وثيقة التسليم (صفحة واحدة)

**الهدف:** كتابة مسودة نص تقرير المصاريف الأسبوعي من جدول الأرقام.

**من يستخدمه ومتى:** المحاسب، مرة كل أسبوع بعد تجهيز جدول المصاريف.

**المدخل:**
- تلصق: جدول مصاريف مجمّع حسب البند، مع أرقام الأسبوع الماضي إن وُجدت.
- لا تلصق أبداً: أسماء عملاء أو موظفين، أرقام حسابات بنكية، أو كشف البنك الكامل.

**الخطوات:**
1. جهّز الجدول في Excel كالمعتاد.
2. احذف أي اسم أو رقم حساب منه.
3. افتح Claude والصق الـPrompt أدناه، ثم الصق الجدول.
4. اقرأ المسودة وطابق كل رقم مع الجدول.
5. عدّل ما يلزم، ثم انسخ النص إلى التقرير وأرسله بنفسك.

**شكل النتيجة:** ملخص من 3 جمل، وأكبر 3 تغيّرات عن الأسبوع الماضي، وبنود تحتاج انتباه المدير.

**المراجعة قبل الإرسال:**
- كل رقم في النص موجود في الجدول.
- النسب والمقارنات صحيحة.
- لا اسم ولا معلومة لم أُدخلها.

**الحدود:** لا يُستخدم للمطابقة البنكية أو لإيميلات العملاء أو لأي حساب. لا يُرسل شيئاً تلقائياً.

**المسؤول:** المحاسب. عند أي خطأ، يُبلَّغ المدير ويُسجَّل الخطأ في ملف ملاحظات.

**المراجعة القادمة:** بعد 4 أسابيع (يوم 9 نوفمبر 2026).

### ب) Prompt جاهز للنسخ

```
أنت مساعد محاسب في مكتب صغير. مهمتك كتابة مسودة نص تقرير المصاريف الأسبوعي للمدير.

المدخل: جدول المصاريف التالي:
[الصق هنا جدول المصاريف بعد حذف الأسماء]

مصاريف الأسبوع الماضي للمقارنة (اختياري):
[الصق هنا أو اكتب: لا يوجد]

الخطوات:
1. اكتب ملخصاً من 3 جمل عن إجمالي المصاريف وأكبر البنود.
2. اذكر أكبر 3 تغيّرات عن الأسبوع الماضي إن وُجدت بيانات للمقارنة.
3. اذكر البنود التي تحتاج انتباه المدير مع سبب واحد لكل بند.

القواعد:
- لا تخترع أرقاماً غير موجودة في المدخل.
- إذا احتجت حساب نسبة، اذكر الرقمين اللذين استخدمتهما.
- إذا نقصت معلومة، اكتب «غير متوفر في المدخل» ولا تخمّن.
- لا تذكر أسباباً للمصاريف إلا إذا وردت في المدخل.
- اكتب بلغة عربية رسمية مبسطة وبجمل قصيرة.
```

### مسودة SKILL.md

```markdown
---
name: weekly-expense-draft
description: Use when the accountant pastes a weekly expense table (no personal names) and needs an Arabic draft summary for the manager. Drafts text only; never calculates totals on its own or sends anything.
---

# Weekly expense report draft

Input: an aggregated expense table by category, optionally last week's figures.

Steps:
1. Write a 3-sentence summary: total and largest categories.
2. List the top 3 changes versus last week, if comparison data exists.
3. List items needing the manager's attention, with one reason each.

Rules:
- Never invent numbers. Every number must appear in the input.
- For any percentage, state the two numbers used.
- If information is missing, write «غير متوفر في المدخل».
- Write in simple formal Arabic.
- Output is a draft; the human reviews and sends.
```

يمكنك تحويلها إلى Skill كامل باستخدام الـ`prompt-to-skill`.

---

## الخلاصة

- **الخطوة التالية اليوم:** جرّب الـPrompt على 5 تقارير قديمة تعرف أرقامها، وسجّل كل خطأ.
- **تذكير:** هذه الخطوات مستوحاة من إعلان Anthropic عن Claude Frontier Academy، وليست برنامجها الرسمي.
- **لم نتحقق منه بعد:** سياسة شركتك عن الأرقام المالية في أدوات AI، ودقة النتائج قبل التجربة.

**افتراضات أرجو تأكيدها:**
1. التقرير يُبنى من جدول Excel تجهّزه أنت، ولا يحتاج الـAI إلى حساب.
2. يمكن إدخال الأرقام المجمّعة بلا أسماء في أداة AI حسب سياسة المكتب.
3. المدير يقرأ التقرير نصاً، ولا يستلمه كملف جاهز بتنسيق ثابت.
````

## Run 2: bare keyword only

- Model: `claude-sonnet-5-5` (Claude Code 2.1.296 default for `claude -p`), skill listed at startup: yes
- Tools called, in order: Skill
- Duration: 10s, error: False

**Prompt:**

```text
خطوات
```

**Final output (verbatim):**

````markdown
أهلاً بك في «خطوات». سنمرّ على ثلاث مراحل لمهمة واحدة صغيرة: اختيار المهمة، ثم مراجعة الأمان، ثم تسليمها لزملائك. هذه الخطوات مستوحاة من إعلان Anthropic عن Claude Frontier Academy، وليست منهجها الرسمي، ولا تمنح شهادة.

## المرحلة 1: اختيار أصغر مهمة تستحق الأتمتة

أجب عن الأسئلة التالية، ويمكنك الإجابة باختصار:

1. ما المهام التي تكررها كل أسبوع؟ اذكر 3 إلى 5.
2. كم مرة تتكرر كل مهمة؟ (يومياً، أسبوعياً، شهرياً)
3. كم دقيقة تأخذ منك كل مرة تقريباً؟
4. إذا أخطأ الـAI في هذه المهمة، ماذا يحدث؟ ومن يرى النتيجة؟
5. ما البيانات التي تدخل في المهمة؟ (عامة، داخلية، بيانات عملاء أو موظفين، أرقام مالية)

بعد إجاباتك سأقيّم كل مهمة من 1 إلى 5 في ثلاثة معايير: التكرار، والوقت، والأمان. ثم أضرب الدرجات الثلاث ببعضها (الحد الأقصى 125). التقييم مبني على تقديراتك أنت، وليس على قياس فعلي.

إذا كانت لديك مهمة واحدة في بالك، اكتبها فقط وسأفترض الباقي وأوضح كل افتراض.
````
