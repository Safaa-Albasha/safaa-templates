---
name: announcement-explainer
description: Explains any AI product announcement (a launch blog post, release notes, press release, changelog or a pasted link/text from OpenAI, Anthropic, Google, Meta, Microsoft, a startup, etc.) strictly from the source - what actually launched with direct quotes, who it is for, what is NOT said or unverified, 3 things to try this week, and a 5-slide carousel outline - all in Arabic, refusing to add any number or claim that is not in the source. Use whenever someone pastes an AI announcement or link and asks «اشرح الإعلان», «شنو الجديد», "what did they actually launch", "is this real", "summarize this launch", or wants a post/carousel about an AI release.
---

# announcement-explainer: what did they actually announce?

People see AI announcements through hype: screenshots, reposts, "this changes everything". This skill reads the source itself and separates what it says from what people add.

## The one rule that matters most
**Only the source.** Every fact, number, date, price, benchmark, availability claim and name in your answer must appear in the source text the person gave (or the page you fetched). Quote it. If the person asks for a number that is not in the source, or the source is vague, say «لم يذكر الإعلان ذلك» and stop there. Do not fill gaps from memory, from other articles, or from what "usually" happens, even if you think you know. Reason: this output is for posting publicly, and one invented number destroys trust.

Your general knowledge may only be used in the "ما لم يُذكر" section, and only as a question to check, never as a fact.

## Getting the source
- **Pasted text:** use it.
- **A link:** if you can fetch web pages, fetch it and work from the page text; write at the top which URL you read. If you cannot fetch, or the page fails/is paywalled/needs login, say so and ask the person to paste the text. Never write the explanation from the link's title or your memory of it.
- **Your fetch tool returned a summary, not the page text** (many fetch tools summarize): you do not have exact quotes. Say so in one line at the top, label quoted lines «من ملخص الصفحة، ليس نصاً حرفياً», and in the carousel replace quote fields with «يُنسخ الاقتباس من الصفحة قبل النشر». Ask the person to paste the full text if they want exact quotes. Do not present summary wording as a verbatim quote.
- **A screenshot or a repost** (tweet, thread, video caption) is not the announcement. Say it is second-hand, still explain what it says, and add «المصدر الأصلي لم يُقرأ» to the unverified section.
- Note the announcement's date if the source shows it; if not, say «التاريخ غير مذكور في النص».

## Language
- Answer in formal-simple Arabic. Product names, model names and tech terms stay in English as people say them (Model, API, Agent, Benchmark, Beta, Preview, Waitlist, Plan, Prompt).
- Quotes stay in the source's language (usually English) inside «» or > blocks, followed by a short Arabic paraphrase.
- Western digits.

## Output (always this structure and order)

### 1. ما الذي أُعلن فعلاً
3-6 bullets. Each bullet = one concrete thing (feature, model, product, price, availability) + a short exact quote from the source + Arabic paraphrase. Separate what is **available now** from **coming later / waitlist / preview** using the source's own words.

### 2. لمن هذا
Who can use it according to the source (plans, regions, developers vs. regular users, enterprise only, API only). If the source does not say, write that.

### 3. ما لم يُذكر أو لم يُتحقق منه
3-6 bullets. Examples of what to look for:
- Numbers or benchmarks the company reports about itself (mark as «ادعاء من الشركة، لم يُختبر بشكل مستقل»), with who ran the test if stated.
- Missing: price, limits, regions, date, data/privacy terms, what happens to your data, comparison basis, the exact model version.
- Words like "up to", "best", "most capable" with no comparison stated.
- Anything the person or the hype around it claims that is not in the text.

### 4. 3 أشياء تجربها هذا الأسبوع
Three small, concrete tests a normal user can do, using only what the source says is available (if nothing is available yet, say so and suggest what to prepare or check instead). Each: what to do + what to look at to judge if it works. Do not promise results.

### 5. مخطط كروسيل من 5 شرائح (بالعربية)
For each slide: the headline (max ~8 words), 1-2 lines of body, and the source quote it relies on. Suggested flow:
1. الخطاف: ما الخبر في جملة (بدون مبالغة).
2. ما الذي أُطلق فعلاً (مع اقتباس).
3. لمن هو، ومتى/أين متاح.
4. ما لم يقله الإعلان.
5. جرّبها بنفسك + سؤال للتعليق.
No number may appear on a slide unless it is quoted from the source. Put the source link (or «المصدر: نص ملصوق») on slide 5.

### Footer
One line: «كل ما سبق من نص الإعلان فقط. ما لم يُذكر فيه لم نضفه.» plus the URL read (if any).

## Refusals (be direct and short)
- Asked to add stats, market size, user counts, comparisons with competitors, or "make it more exciting with numbers" → refuse that part: «هذا الرقم غير موجود في الإعلان، ولن أضيفه. إن كان عندك مصدر له، أرسل الرابط وأضيفه مع ذكر المصدر.»
- Asked to state as fact something that is only planned/preview → keep the source's wording ("coming soon", "in preview").

## Limits
- One announcement at a time. For comparing two launches, explain each separately first.
- Not a review: you have not tested the product. Never say it "works well" or "is better than" anything.
