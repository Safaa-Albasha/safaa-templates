# safaa-templates

قوالب مجانية وClaude Skills من **SAFAA.IO** (صفاء الباشا).
كل قالب صفحة واحدة تملؤها بنفسك أو مع Claude، في المشاريع والجودة والبيانات والعروض والبناء بالذكاء الاصطناعي.

اقرأها وانسخها ونزّلها مرتبة على **[safaa.io/templates](https://safaa.io/templates/)**، ومعها الدليل PDF: [`guide/safaa-templates-guide.pdf`](guide/safaa-templates-guide.pdf).

- القوالب في مجلد [`templates/`](templates).
- الـSkills في مجلد [`skills/`](skills)، وملفاتها المضغوطة في [`dist/`](dist). طريقة التثبيت: [`INSTALL-ar.md`](INSTALL-ar.md).

## القوالب

### مشاريع وجودة

| القالب | ماذا يفعل | لمن | الملف |
|---|---|---|---|
| خريطة الـAI في المشروع | أين يساعد الـAI في كل مرحلة من المشروع، وأين لا تعتمد عليه، وكيف تتحقق | مدير مشروع أو فريق | [ai-project-map.md](templates/ai-project-map.md) |
| جدول CTQ | يحوّل ما يريده العميل إلى خصائص تُقاس قبل كتابة الـPrompt | من يعتمد على مخرجات AI في عمله | [ctq-table.md](templates/ctq-table.md) |
| ورقة DMAIC لـPrompt | يحسّن Prompt واحداً بخطوات Six Sigma: عرّف، قِس، حلّل، حسّن، ثبّت | من عنده Prompt يستعمله كل يوم | [dmaic-prompt-sheet.md](templates/dmaic-prompt-sheet.md) |
| FMEA لميزة AI | يعدّد طرق فشل الميزة قبل أن تفشل أمام العميل، ويرتّبها بالأولوية | فريق منتج أو جودة | [fmea-ai.md](templates/fmea-ai.md) |

### بيانات وتحليل

| القالب | ماذا يفعل | لمن | الملف |
|---|---|---|---|
| ورقة سؤال البيانات | تحدد القرار والسؤال والمقياس قبل أن تفتح أي ملف | من يطلب تحليلاً أو يجريه | [data-question-brief.md](templates/data-question-brief.md) |
| قائمة تنظيف البيانات | 8 فحوص للبيانات مع سجل لكل تغيير | من يجهّز ملف Excel أو CSV | [data-cleaning-checklist.md](templates/data-cleaning-checklist.md) |
| قائمة الاستكشاف الأولي (EDA) | خطوات أول نظرة على البيانات، وأخطاء التحليل الشائعة | محلل مبتدئ | [eda-checklist.md](templates/eda-checklist.md) |
| التحقق من تحليل الـAI | 7 خطوات قبل أن تقبل رقماً حسبه الـAI | من يحلل البيانات مع AI | [ai-analysis-verification.md](templates/ai-analysis-verification.md) |
| قبل أن تنشر رقماً من AI | 5 خطوات للتحقق من رقم أعطاك إياه AI، مع مثال من تجربتنا | أي شخص ينشر أو يقرر برقم | [number-check.md](templates/number-check.md) |
| Prompt صفحة الهبوط | طلب جاهز يبني صفحة هبوط عربية بـTailwind CSS، مع فحص قبل النشر | صاحب مشروع يريد صفحة بسرعة | [landing-page-prompt.md](templates/landing-page-prompt.md) |
| اختيار الرسم | أي رسم يناسب رسالتك، وماذا تتجنب | من يعرض أرقاماً | [chart-chooser.md](templates/chart-chooser.md) |
| مذكرة التحليل | تحوّل نتائج التحليل إلى توصية في صفحة واحدة | من يرفع تحليلاً لصاحب قرار | [analysis-memo.md](templates/analysis-memo.md) |

### عروض

| القالب | ماذا يفعل | لمن | الملف |
|---|---|---|---|
| هيكل العرض | الجمهور والرسالة وقصة SCQA قبل أن تفتح الشرائح | من يحضّر عرضاً | [presentation-storyline.md](templates/presentation-storyline.md) |
| قائمة فحص الشرائح | فحص الرسالة والبيانات والتصميم قبل العرض | من يراجع عرضاً | [slide-checklist.md](templates/slide-checklist.md) |

### بناء بالذكاء الاصطناعي

| القالب | ماذا يفعل | لمن | الملف |
|---|---|---|---|
| بطاقة المشروع | تعرّف Claude بمشروعك مرة واحدة: من أنتم، جمهوركم، نبرتكم، وما الممنوع. فيها طلب جاهز ليسألك Claude بدل أن تكتب | صاحب مشروع صغير أو متوسط | [project-card.md](templates/project-card.md) |
| PRD لميزة AI | وثيقة صفحة واحدة لميزة AI: المستخدم، المدخل، المخرج، معيار النجاح، الضوابط | مدير منتج | [ai-prd.md](templates/ai-prd.md) |
| مجموعة اختبار ذهبية | أمثلة حقيقية تقيس بها أي تغيير في الموديل أو الـPrompt بالمقياس نفسه | من يبني أو يقارن أدوات AI | [eval-golden-set.md](templates/eval-golden-set.md) |
| بطاقة الحكم | نتيجة أي تجربة في بطاقة: المعيار، حجم العينة n، النجاح والفشل، الحكم | من يجرّب أداة أو موديل | [verdict-card.md](templates/verdict-card.md) |
| لوحة بناء Skill | تصمّم Skill وتختبره على 10 مدخلات قبل أن تشاركه | من يتعلم بناء Skills | [skill-building-canvas.md](templates/skill-building-canvas.md) |

## الـSkills

| Skill | ماذا يفعل | حالة الاختبار |
|---|---|---|
| [`khutuwat`](skills/khutuwat) (خطوات) | يختار معك مهمة صغيرة متكررة في عملك، يراجع أمانها، ويكتب وثيقة تسليم وPrompt جاهزاً | فحص سريع: تشغيلتان، n=1 لكل واحدة |
| [`prompt-to-skill`](skills/prompt-to-skill) | يحوّل Prompt تكرره كل يوم إلى Skill كامل، ويجرّبه مرة واحدة | فحص سريع: تشغيلتان، n=1 لكل واحدة |
| [`announcement-explainer`](skills/announcement-explainer) | يشرح إعلان AI من نصه فقط: ماذا أُطلق، وماذا لم يُذكر | فحص سريع: تشغيلتان، n=1 لكل واحدة |

الفحص السريع ليس قياساً للجودة. التفاصيل في ملف `TEST-RESULTS.md` داخل مجلد كل Skill.
التثبيت (تطبيق Claude أو Claude Code): [`INSTALL-ar.md`](INSTALL-ar.md).

## مكتبة الأسبوع: Prompts التصميم
طلب جاهز لكل مكتبة من سلسلة «مكتبة الأسبوع»، يبني صفحة عربية لمشروعك بالمكتبة نفسها، ومع كل طلب 3 فحوص قبل النشر. كلمة التعليق: «تصميم».

| # | المكتبة | الملف |
|---|---|---|
| 01 | Tailwind CSS | [landing-page-prompt.md](templates/landing-page-prompt.md) |
| 02 | shadcn/ui | [shadcn.md](templates/library-prompts/shadcn.md) |
| 03 | Bootstrap | [bootstrap.md](templates/library-prompts/bootstrap.md) |
| 04 | daisyUI | [daisyui.md](templates/library-prompts/daisyui.md) |
| 05 | Material UI | [mui.md](templates/library-prompts/mui.md) |
| 06 | Ant Design | [antd.md](templates/library-prompts/antd.md) |
| 07 | Chakra UI | [chakra.md](templates/library-prompts/chakra.md) |
| 08 | three.js | [three.md](templates/library-prompts/three.md) |
| 09 | GSAP | [gsap.md](templates/library-prompts/gsap.md) |
| 10 | Motion | [motion.md](templates/library-prompts/motion.md) |

## كلمات التعليق

إذا علّقت بكلمة على أحد منشوراتنا، فهذا هو الملف الذي تصلك إليه:

| الكلمة | الملف |
|---|---|
| قوالب | هذه الصفحة (كل القوالب) |
| DMAIC | [dmaic-prompt-sheet.md](templates/dmaic-prompt-sheet.md) |
| CTQ | [ctq-table.md](templates/ctq-table.md) |
| معيار | [eval-golden-set.md](templates/eval-golden-set.md) |
| بطاقة | [project-card.md](templates/project-card.md) |
| حكم | [verdict-card.md](templates/verdict-card.md) |
| رقم | [number-check.md](templates/number-check.md) |
| تصميم | [landing-page-prompt.md](templates/landing-page-prompt.md) وملفات [library-prompts](templates/library-prompts/) |
| خطوات | [skills/khutuwat](skills/khutuwat) · [khutuwat.zip](dist/khutuwat.zip) |
| سكل | [skills/prompt-to-skill](skills/prompt-to-skill) · [prompt-to-skill.zip](dist/prompt-to-skill.zip) |
| إعلان | [skills/announcement-explainer](skills/announcement-explainer) · [announcement-explainer.zip](dist/announcement-explainer.zip) |

## كيف تستعمل قالباً مع Claude

1. **افتح القالب** وانسخ نصه، أو نزّل الملف.
2. **الصقه في Claude** واكتب: «املأ هذا القالب معي. اسألني سؤالاً واحداً في كل مرة، ولا تفترض أي معلومة لم أقلها.»
3. **راجع النتيجة بنفسك:** كل رقم له مصدر أو n، وما افترضه Claude يُكتب في قائمة منفصلة.

## الرخصة

- **القوالب والنصوص:** [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). استعملها وعدّلها وشاركها، واذكر المصدر: SAFAA.IO - صفاء الباشا.
- **الـSkills:** رخصة MIT.

النص الكامل في [`LICENSE`](LICENSE).
