# طريقة التثبيت

3 Skills من SAFAA.IO: `khutuwat` (خطوات)، `prompt-to-skill`، `announcement-explainer`.
كلها تجيب بالعربية. كلها جُرّبت مرة واحدة فقط (n=1)، فهي فحص سريع وليست مضمونة.

## أ) تطبيق Claude أو Claude.ai

1. نزّل الملف المضغوط للـSkill من مجلد [`dist/`](dist) (مثلاً `khutuwat.zip`). **لا تفك الضغط.**
2. فعّل تنفيذ الكود: **Settings ← Capabilities** ثم شغّل «Code execution and file creation».
   (في حسابات Team وEnterprise يفعّلها مالك المؤسسة أولاً.)
3. اذهب إلى **Customize ← Skills**، اضغط **+** ثم **Create skill** ثم **Upload a skill**، واختر الملف.
4. ابدأ محادثة جديدة واكتب مثلاً: «خطوات» ثم صف عملك.

> مسار القوائم منقول من صفحة مساعدة Anthropic «Using Skills in Claude» كما ظهرت في 12 أكتوبر 2026. قد تتغير أسماء القوائم.

## ب) Claude Code

**الطريقة 1: نسخ المجلد**
```bash
mkdir -p ~/.claude/skills
cp -r skills/khutuwat skills/prompt-to-skill skills/announcement-explainer ~/.claude/skills/
```
ثم افتح Claude Code من جديد.

**الطريقة 2: Plugin (الثلاثة مرة واحدة)**
داخل Claude Code:
```
/plugin marketplace add Safaa-Albasha/safaa-templates
/plugin install safaa-skills@safaa-io
```
أو بمسار محلي بعد تنزيل المستودع: `/plugin marketplace add ./safaa-templates`

## تأكد أنه يعمل
اسأل Claude: «ما الـSkills المتاحة لديك؟» يجب أن ترى الأسماء الثلاثة.
