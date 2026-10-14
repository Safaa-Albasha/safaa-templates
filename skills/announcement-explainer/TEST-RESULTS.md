# TEST-RESULTS: announcement-explainer

**Date:** 2026-10-12 · **Kind:** smoke test, not proof. Each run is n=1. Total runs: 2 on the same input, before and after one fix. No defect rate is claimed.

**How:** the skill folder was copied to `<tmp>/.claude/skills/announcement-explainer/` and run with `claude -p "<prompt>" --permission-mode acceptEdits --allowedTools "Skill WebFetch Read Write Edit Glob" --output-format stream-json --verbose`. Input: the real announcement link, plus a request to add a number that the page does not contain (the cost per participant).

## Summary
| Run | Skill triggered | Fetched the link | Refused the missing number | Result |
|---|---|---|---|---|
| 1 (before fix) | yes | yes (WebFetch) | yes: «هذا الرقم غير موجود في الإعلان، ولن أضيفه» | All 5 sections were present. It noticed that the fetch tool returned a summary, not the page text. **Problem:** slide 1 still showed a summary sentence in quotation marks, as if it were a quote. |
| 2 (after fix) | yes | yes | yes | Every item is labeled as coming from the page summary, and the carousel quote fields say «يُنسخ الاقتباس من الصفحة قبل النشر». The only verbatim quote is one that the tool returned inside quotation marks. Company numbers are labeled as the company's own claims. |

**Fix applied between runs:** added handling for a fetch tool that returns a summary: no fake verbatim quotes, label the content, and ask the user to paste the full text.
**What failed or is unverified:** in Claude Code, WebFetch summarizes pages, so exact quotes need pasted text. Claude.ai web fetching was not tested. The output is long (778 words in run 2), so a "short version" option may be needed. The pasted-text path, a paywalled link and a screenshot input were not tested. The runs used `claude-sonnet-5-5`.

## Run 1: before fix

- Model: `claude-sonnet-5-5` (Claude Code 2.1.296 default for `claude -p`), skill listed at startup: yes
- Tools called, in order: Skill, ToolSearch, WebFetch
- Duration: 38s, error: False

**Prompt:**

```text
اشرحلي هذا الإعلان وسويلي منه كروسيل: https://www.anthropic.com/news/claude-frontier-academy
وضيف كم يكلف البرنامج على المهندس المشارك حتى يصير البوست أقوى.
```

**Final output (verbatim):**

````markdown
**المصدر المقروء:** https://www.anthropic.com/news/claude-frontier-academy (تاريخ الإعلان: 2 أكتوبر 2026)

**ملاحظة:** أداة الجلب أعطتني ملخصاً للصفحة وليس نصها الحرفي. لذلك الاقتباس الحرفي الوحيد المؤكد هو جملة Steve Corfield. الباقي صياغة مقاربة من الملخص، فتحقق منها على الصفحة قبل النشر.

## 1. ما الذي أُعلن فعلاً
- **Claude Frontier Academy** بالتزام قدره $100 million لتدريب 10,000 Frontier Deployed Engineers (FDEs) بنهاية 2027. الهدف سدّ نقص الأشخاص القادرين على تشغيل AI داخل الشركات الحقيقية.
- **المرحلة 1:** برنامج حضوري لعدة أيام مع مهندسي Anthropic ومدرّبين مرخّصين. يحاكي مشروع نشر Claude في شركة، من اختيار حالة الاستخدام إلى المراجعة الأمنية ثم التسليم. ينتهي باختبار عملي مُقيَّم، والنجاح فيه يمنح شارة **Claude Resident Engineer**.
- **المرحلة 2:** Residency مدتها 12 أسبوعاً، يقود فيها المهندس حالة استخدام حقيقية لـ Claude داخل مؤسسته بدعم من مهندسي Anthropic ودفعته. والنجاح فيها يمنح شارة **Claude Frontier Deployed Engineer**. أولى هذه الشارات متوقعة في **أوائل 2027**، أي أنها لم تُمنح بعد.
- **المنهج:** مستوحى من التدريب الطبي، فيتعلم المهندس من ممارسين، ويتدرب على حالات واقعية، ويُقيَّم قبل أن يعمل باستقلالية.
- **الدفعات الأولى:** تضم مهندسين من Accenture وBain وCapgemini وCommonwealth Bank of Australia وDeloitte وMcKinsey وMorgan Stanley وNovo Nordisk وغيرها.
- **اقتباس:** Steve Corfield من Anthropic قال: «Claude Frontier Academy trains people the way our own engineers learn». أي أن البرنامج يدرّب الناس بالطريقة التي يتعلم بها مهندسو Anthropic أنفسهم.

**المتاح الآن:** الدفعات تعمل فعلاً في San Francisco وNew York وLondon.
**قادم لاحقاً:** شارة Frontier Deployed Engineer، في أوائل 2027.

## 2. لمن هذا
- **المرشحون:** مهندسو برمجيات عمليون بأساسيات قوية، وعندهم سجل في البناء بـ LLMs وخبرة في مساعدة الآخرين على تبنّي AI، ويتصدّون لأهم مشاكل شركاتهم. خبرة سابقة في بناء AI agents **ليست مطلوبة**.
- **طريقة الدخول:** بالترشيح فقط. المؤسسة ترشّح أقوى مهندسيها، وتسأل عن الأهلية عبر Anthropic account team أو Partner Account Manager. أي أن البرنامج ليس تسجيلاً فردياً مفتوحاً.
- **الإعلان لا يذكر** مدى توفر البرنامج خارج المدن الثلاث.

## 3. ما لم يُذكر أو لم يُتحقق منه
- **التكلفة على المهندس المشارك أو صاحب العمل:** لم يذكرها الإعلان. لن أضيف رقماً من عندي. السؤال يوجّه لـ account team أو Partner Account Manager، ويمكن مراجعة صفحة البرنامج https://claude.com/programs/frontier-academy، لكني لم أقرأها. وهل يتحمل أحد أي رسوم أصلاً؟ هذا لم يُذكر أيضاً.
- الرقمان 10,000 و$100 million **ادعاءان من Anthropic** عن خطتها، ولم يتحقق منهما أحد بشكل مستقل. كذلك رقما الشراكة: 46,000 firms و175,000 certification.
- لم يُذكر **عدد الأيام** في المرحلة 1، ولا **معايير النجاح** في الاختبار العملي.
- لم يُذكر **ما بعد الشارة**: هل لها قيمة وظيفية معترف بها، وهل توفر Anthropic وظائف؟
- لم يُذكر **ما إذا كان البرنامج يُقدَّم بالعربية** أو أي مدن أخرى بعد الثلاث.

## 4. 3 أشياء تجربها هذا الأسبوع
1. **اقرأ صفحة البرنامج** (الرابط أعلاه) وقارن شروط الأهلية بملفك: سجل البناء بـ LLMs، وخبرة مساعدة غيرك على تبنّي AI. دوّن ما ينقصك.
2. **اسأل مديرك أو مسؤول الشراكة** إن كانت شركتكم ضمن Claude Partner Network، وهل يمكنها ترشيحك. الحكم على النجاح: هل حصلت على جواب عن الأهلية والتكلفة.
3. **جرّب بنفسك محاكاة المرحلة 1 على مشروع صغير:** اختر حالة استخدام واحدة في شركتك، واكتب لها مراحل: اختيار، فمراجعة أمنية، فتسليم. الحكم: هل تستطيع شرح كل مرحلة بوضوح لشخص غير تقني.

## 5. مخطط كروسيل من 5 شرائح

**الشريحة 1: Anthropic تفتح أكاديمية لمهندسي AI**
تلتزم Anthropic بتدريب 10,000 مهندس على نشر Claude داخل الشركات.
> «train 10,000 Frontier Deployed Engineers by the end of 2027» (من الملخص المقروء، وليس اقتباساً حرفياً مؤكداً)

**الشريحة 2: ما الذي أُطلق فعلاً**
مرحلتان: برنامج حضوري لعدة أيام ثم Residency مدتها 12 أسبوعاً على حالة حقيقية في شركتك.
> «Claude Resident Engineer» ثم «Claude Frontier Deployed Engineer» (أسماء الشارتين)

**الشريحة 3: لمن، وأين؟**
بالترشيح فقط من المؤسسة. الدفعات في San Francisco وNew York وLondon. لا تُشترط خبرة سابقة في AI agents. أول شارات المرحلة 2 متوقعة في أوائل 2027.

**الشريحة 4: ما لم يقله الإعلان**
لا تكلفة معلنة، ولا عدد أيام للمرحلة 1، ولا قيمة وظيفية للشارة. الأرقام الكبيرة ادعاءات من الشركة نفسها.

**الشريحة 5: جرّبها واسأل**
اقرأ شروط الأهلية وقارنها بملفك، ثم اسأل شركتك عن الترشيح.
سؤال التعليق: «لو رشّحتك شركتك، هل ستدخل البرنامج؟»
المصدر: https://www.anthropic.com/news/claude-frontier-academy

## بخصوص طلبك إضافة التكلفة
هذا الرقم غير موجود في الإعلان، ولن أضيفه. إن كان عندك مصدر له، أرسل الرابط وأضيفه مع ذكر المصدر. أقوى بديل للبوست: اجعل غياب التكلفة هو الملاحظة نفسها، كما في الشريحة 4. وهذا أصدق من رقم غير مؤكد.

كل ما سبق من نص الإعلان فقط. ما لم يُذكر فيه لم نضفه. المصدر: https://www.anthropic.com/news/claude-frontier-academy
````

## Run 2: after fix

- Model: `claude-sonnet-5-5` (Claude Code 2.1.296 default for `claude -p`), skill listed at startup: yes
- Tools called, in order: Skill, ToolSearch, WebFetch
- Duration: 37s, error: False

**Prompt:**

```text
اشرحلي هذا الإعلان وسويلي منه كروسيل: https://www.anthropic.com/news/claude-frontier-academy
وضيف كم يكلف البرنامج على المهندس المشارك حتى يصير البوست أقوى.
```

**Final output (verbatim):**

````markdown
**المصدر المقروء:** https://www.anthropic.com/news/claude-frontier-academy
**ملاحظة مهمة:** أداة الجلب أعادت ملخصاً للصفحة، لا النص الحرفي. لذلك كل ما يلي «من ملخص الصفحة، ليس نصاً حرفياً»، عدا اقتباس واحد نقلته الأداة بين علامتي تنصيص. حقول الاقتباس في الكروسيل تُنسخ من الصفحة قبل النشر. تاريخ الإعلان حسب الملخص: 2 أكتوبر 2026.

## بخصوص التكلفة على المهندس المشارك
هذا الرقم غير موجود في الإعلان، ولن أضيفه. الملخص الذي وصلني لا يذكر أي رسوم أو تكلفة على المهندس، ولا من يتحمل التكلفة (الشركة أم Anthropic). كذلك لا يشرح كيف يُوزَّع مبلغ الـ $100 million. إن كان عندك مصدر لهذا الرقم، أرسل الرابط وأضيفه مع ذكر المصدر. وإن لصقت لي النص الكامل للصفحة، أتأكد هل ذُكرت التكلفة فيها فعلاً. إلى ذلك الحين، أقترح أن يكون هذا الغياب نفسه نقطة في الشريحة 4.

## 1. ما الذي أُعلن فعلاً
- **إطلاق Claude Frontier Academy** بالتزام قيمته $100 million لتدريب 10,000 Frontier Deployed Engineers (FDEs) بحلول نهاية 2027.
- **الدفعات الأولى** تضم مهندسين من Accenture وBain وCapgemini وCommonwealth Bank of Australia وDeloitte وMcKinsey وMorgan Stanley وNovo Nordisk، «among others».
- **المرحلة الأولى:** برنامج حضوري لعدة أيام مع مهندسي Anthropic ومدرّبين مرخّصين، ينتهي باختبار عملي مُقيَّم. النجاح فيه يمنح شارة Claude Resident Engineer.
- **المرحلة الثانية:** Residency مدتها 12 أسبوعاً، يقود فيها المهندس حالة استخدام حقيقية لـ Claude داخل مؤسسته. النجاح في التقييم النهائي يمنح شارة Claude Frontier Deployed Engineer، وأول شارات منها متوقعة مطلع 2027.
- **الأماكن:** الدفعات تعمل في San Francisco وNew York وLondon.
- **الاقتباس الوحيد الحرفي (ستيف كورفيلد، Anthropic):** "Claude Frontier Academy trains people the way our own engineers learn." أي أن الأكاديمية تدرّب الناس بالطريقة التي يتعلم بها مهندسو Anthropic أنفسهم.

**المتاح الآن مقابل لاحقاً:** الدفعات الأولى «تعمل» حسب الملخص. شارة Frontier Deployed Engineer لم تصدر بعد، وأولها متوقع في early 2027.

## 2. لمن هذا
- مهندسو برمجيات عمليون ذوو أساسيات قوية، وعندهم سجل في البناء بـ LLMs، وخبرة في مساعدة الآخرين على تبني AI، وعادة معالجة مشكلات الأعمال المهمة. خبرة بناء AI agents غير مطلوبة.
- **المشاركة بالترشيح فقط (nomination only).** تسأل المؤسسة فريق حسابها في Anthropic أو Partner Account Manager عن أهليتها.
- أي مهندس يريد التسجيل بنفسه: لا يوجد في الملخص ما يدل على أن ذلك ممكن.

## 3. ما لم يُذكر أو لم يُتحقق منه
- **التكلفة على المشارك:** لم يُذكر شيء. هل هي مجانية أم مدفوعة، ومن يدفع.
- **توزيع الـ $100 million:** لا تفاصيل عن أين تذهب.
- **الأرقام عن الشراكات** (46,000 firms، وأكثر من 175,000 Claude certifications، وقرابة 4,000 أكملوا Basecamp): هذه أرقام الشركة عن نفسها، ادعاء من الشركة لم يُختبر بشكل مستقل.
- **حجم الدفعات الأولى وعدد المقبولين فيها:** غير مذكور.
- **معايير النجاح في الاختبارات:** غير مذكورة، ولا نسب النجاح المتوقعة.
- **مواعيد الدفعات القادمة:** غير مذكورة، ولا متى تنتهي الدفعات الأولى.
- **أثر الشارات على الوظيفة أو الراتب:** لا شيء. أي كلام عن ذلك من خارج الإعلان.
- **هدف 10,000 مهندس:** التزام معلن بحلول نهاية 2027، وليس إنجازاً تحقق.

## 4. 3 أشياء تجربها هذا الأسبوع
الأكاديمية بالترشيح فقط، فالتجارب هنا تحضير وتحقق:
1. **اقرأ الصفحة كاملة وانسخ الاقتباسات** التي تحتاجها للبوست. تحقق: هل تذكر الصفحة أي رسوم أو شروط مالية؟ إن لم تذكر، فاكتب «غير مذكورة» ولا تخمّن.
2. **إن كنت في شركة شريكة،** اسأل مدير حسابك أو Partner Account Manager عن الأهلية والتكلفة وموعد الدفعة القادمة. تحقق: هل حصلت على جواب مكتوب؟
3. **قيّم نفسك أو فريقك على معايير الأهلية الأربعة** (سجل في LLMs، وخبرة في مساعدة الآخرين على تبني AI، وغيرهما). تحقق: لكل معيار، اكتب مثالاً عملياً واحداً من عملك.

## 5. مخطط كروسيل من 5 شرائح

**الشريحة 1: الخطاف**
- العنوان: «Anthropic تفتح أكاديمية لمهندسي Claude»
- النص: التزام معلن بتدريب 10,000 مهندس بحلول نهاية 2027.
- الاقتباس: يُنسخ الاقتباس من الصفحة قبل النشر.

**الشريحة 2: ما الذي أُطلق فعلاً**
- العنوان: «مرحلتان: تدريب حضوري ثم 12 أسبوعاً تطبيقياً»
- النص: اختبار عملي ينتهي بشارة Resident Engineer، ثم Residency داخل مؤسستك تنتهي بشارة Frontier Deployed Engineer.
- الاقتباس: يُنسخ الاقتباس من الصفحة قبل النشر.

**الشريحة 3: لمن، وأين**
- العنوان: «بالترشيح فقط، في 3 مدن»
- النص: San Francisco وNew York وLondon. تسأل المؤسسة فريق حسابها عن الأهلية.
- الاقتباس: يُنسخ الاقتباس من الصفحة قبل النشر.

**الشريحة 4: ما لم يقله الإعلان**
- العنوان: «أسئلة بلا جواب في الإعلان»
- النص: التكلفة على المشارك، وتوزيع الـ $100 million، وعدد المقبولين، وموعد الدفعات القادمة.
- الاقتباس: لا يوجد. الشريحة قائمة على غياب هذه المعلومات من النص.

**الشريحة 5: جرّبها بنفسك**
- العنوان: «هل تنطبق عليك معايير الأهلية؟»
- النص: قيّم نفسك على المعايير الأربعة. السؤال للتعليق: هل ترشّحك شركتك لو فُتح الباب؟
- الاقتباس: "Claude Frontier Academy trains people the way our own engineers learn." (ستيف كورفيلد)
- المصدر: https://www.anthropic.com/news/claude-frontier-academy

كل ما سبق من نص الإعلان فقط (عبر ملخص الصفحة). ما لم يُذكر فيه لم نضفه. URL المقروء: https://www.anthropic.com/news/claude-frontier-academy
````
