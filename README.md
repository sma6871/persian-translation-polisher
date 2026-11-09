# Persian Translation Polisher (پالایشگر ترجمه و نگارش فارسی)

A modular, agent-ready AI skill that runs an automated quality and refinement pipeline on Persian (Farsi) text. It transforms mechanical, machine-translated, or AI-generated Persian into authentic, fluent, orthographically clean, and technically precise Persian.

---

## 🌟 Upstream Credits & Foundations

This skill incorporates the rules, dictionaries, and research of four essential open-source Persian projects:

1. **[Salsi (صلصی)](https://github.com/pooooooriya/salsi)** by Pooriya ([@pooooooriya](https://github.com/pooooooriya))
   - Principles for replacing unnecessary foreign loanwords with established, natural Persian words.
   - Core philosophy: *Clarity over purity* (وضوح بر خلوص زبانی اولویت دارد).
2. **[Lahne Man (لحن من)](https://github.com/RezaEsmailGol/lahne-man)** by Reza EsmailGol ([@RezaEsmailGol](https://github.com/RezaEsmailGol))
   - Eradicating stereotypical AI cadences, hollow hype words, redundant triads, and robotic padding.
3. **[Persian Writing (دستور خط و نگارش فارسی)](https://github.com/ali2000hos/persian-writing)** by Ali Hosseini ([@ali2000hos](https://github.com/ali2000hos))
   - Rigorous Persian typography, Zero-Width Non-Joiner (ZWNJ / نیم‌فاصله), Unicode normalization (`ی`/`ک`), and eliminating bureaucratic cliches like «می‌باشد».
4. **[Awesome Persian AI Rules](https://github.com/amir-hdri/awesome-persian-ai-rules)** by Amir Heydari ([@amir-hdri](https://github.com/amir-hdri))
   - Universal standards for BiDi (Bidirectional) text stability, invisible punctuation markers (`RLM`/`LRM`), and RTL UI layout engineering.

---

## 🚀 Installation & Integration

### 1. Claude Code
To make this skill available across your Claude Code workflows:
- **Project-level:** Place the folder into your project under `.agents/skills/persian-translation-polisher/` or `.claude/skills/persian-translation-polisher/`.
- **Global-level:** Copy this folder to `~/.claude/skills/persian-translation-polisher/`.
- Claude Code will automatically discover `SKILL.md` when you ask to translate, polish, or generate Persian content.

### 2. Cursor IDE
You can use this skill in Cursor via either `.cursorrules` or Cursor MDC Rules:

#### Option A: Cursor MDC Rule (Recommended for Cursor 0.40+)
Create `.cursor/rules/persian-polisher.mdc`:
```markdown
---
description: Automatically polish and humanize Persian translations and text
globs: **/*.{md,mdx,json,po,ts,tsx,html}
alwaysApply: false
---

# Include instructions from PROMPT.md
```
*(Copy the prompt block from [`PROMPT.md`](./PROMPT.md) into this file).*

#### Option B: Global / Workspace `.cursorrules`
Append the contents of [`PROMPT.md`](./PROMPT.md) directly to your project's `.cursorrules`.

### 3. Google Antigravity / OpenMontage
- This skill is located in `.agents/skills/persian-translation-polisher/`.
- The agent automatically loads `SKILL.md` whenever Persian translation, localization, or copy review is requested.

### 4. Windsurf / Roo Code / Cline
- For Windsurf: Add the contents of [`PROMPT.md`](./PROMPT.md) to your `.windsurfrules`.
- For Roo Code / Cline: Add as a Custom Instruction in the extension settings or in `.clinerules`.

### 5. ChatGPT (Custom Instructions / GPTs) & Claude Projects
- Copy the text inside the code fence in [`PROMPT.md`](./PROMPT.md) and paste it into:
  - **ChatGPT:** "How would you like ChatGPT to respond?"
  - **Claude:** "Project Instructions" or System Prompt.

---

## ⚙️ The 5-Stage Pipeline

When triggered, the assistant applies these stages sequentially:

| Stage | Name | Key Actions | Upstream Influence |
| :---: | :--- | :--- | :--- |
| **1** | **Base Translation & Register** | Select target register (UI Microcopy, Marketing, Technical Docs, Colloquial, SEO), avoid word-for-word translation, place verbs naturally. | — |
| **2** | **Salsi Loanword Handling** | Replace everyday foreign borrowings (آیتم ➔ مورد, آپدیت ➔ به‌روزرسانی, کنسل ➔ لغو). Retain technical terms of art (`API`, `Token`, `Git`). | [Salsi](https://github.com/pooooooriya/salsi) |
| **3** | **Lahne-Man De-Machining** | Eradicate AI openers («در دنیای پرشتاب امروز»), break artificial triads, cut hollow hype (انقلابی, شگفت‌انگیز), eliminate passive voice. | [Lahne Man](https://github.com/RezaEsmailGol/lahne-man) |
| **4** | **Orthography, BiDi & i18n** | Enforce Persian `ی`/`ک`, strict ZWNJ (نیم‌فاصله), fix He-Kasreh, BiDi punctuation order (`RLM`/`LRM`), Persian pluralization (`۵ کاربر`), banish «می‌باشد». | [persian-writing](https://github.com/ali2000hos/persian-writing), [awesome-persian-ai-rules](https://github.com/amir-hdri/awesome-persian-ai-rules) |
| **5** | **Final Pass & Output** | Verify consistency, preserve code/markdown/links, output polished text + 3-8 bullet point changelog (or diagnostic report in check mode). | [Lahne Man](https://github.com/RezaEsmailGol/lahne-man) |

---

## 📂 Package Contents

```
.agents/skills/persian-translation-polisher/
├── SKILL.md                          # Full agent skill specification with triggers & pipeline
├── PROMPT.md                         # Portable system prompt adapter for any LLM
├── README.md                         # Installation guides, documentation & credits
└── references/
    ├── loanword-dictionary.md        # Curated Salsi dictionary of common loanwords & protected terms
    ├── lahne-man-patterns.md         # Anti-machine patterns & AI cliché removal guidelines
    ├── orthography-cheat-sheet.md    # ZWNJ rules, Unicode normalization, punctuation & anti-bureaucracy
    ├── bidi-rtl-engineering.md       # BiDi text stability, LRM/RLM markers & RTL web UI rules
    ├── register-modes.md             # Microcopy, Conversational, SEO & Technical register guides
    └── i18n-pluralization.md         # Persian counting rules, i18n variables & Conventional Commits
```

---

## 🧪 Example Before & After

### Input (Typical Raw AI Translation)
> در دنیای پرشتاب امروز، لازم به ذکر است که شما می‌توانید آیتم‌های مختلف را با کلیک بر روی دکمه سیو ذخیره نمایید. این ابزار انقلابی، سریع، امن و شگفت‌انگیز دارای کاربرد زیادی در پروسه کاری شما می‌باشد و پسورد شما به صورت اتوماتیک کانفیگ می‌گردد.

### Output (Polished via Skill Pipeline)
> شما می‌توانید گزینه‌های مورد نظر خود را با زدن روی «ذخیره» ثبت کنید. این ابزار به مدیریت آسان‌تر کارهایتان کمک می‌کند و رمز عبور شما نیز خودکار تنظیم می‌شود.

### Changelog Generated
- **اصلاح اصطلاحات (سلسی):** جایگزینی «آیتم‌ها» با «گزینه‌ها»، «سیو» با «ذخیره»، «پروسه» با «کارها»، «اتوماتیک» با «خودکار»، و «کانفیگ می‌گردد» با «تنظیم می‌شود».
- **حذف ردپای هوش مصنوعی (لحن من):** حذف مقدمه کلیشه‌ای «در دنیای پرشتاب امروز»، عبارت زاید «لازم به ذکر است که»، و صفت‌های اغراق‌آمیز «انقلابی و شگفت‌انگیز».
- **ساده‌نویسی و دستور خط (persian-writing):** حذف فعل‌های اداری «می‌باشد» و «نمایید»، اصلاح نیم‌فاصله در «کارهایتان»، و استفاده از گیومه فارسی («ذخیره»).
- **اصلاح ساختار فعل:** تبدیل جملات مجهول و سنگین به جملات معلوم، فشرده و طبیعی.

---

## 🛡️ Non-Negotiable Constraints
- **Never break technical assets:** Inline code, code blocks, URLs, markdown links, and HTML anchors remain intact.
- **Never fabricate information:** Do not invent facts, metrics, or sources not present in the original input.
- **Minimal surgical edits:** Do not rewrite well-crafted sentences for the sake of rewriting.
