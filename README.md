# Lecture to Markdown Converter Skill | مهارة تحويل المحاضرات إلى Markdown

<!-- foundry:install:start -->
> **AI agents / وكلاء الذكاء الاصطناعي:** to install, read [INSTALL.md](https://raw.githubusercontent.com/nre-edu/lecture-to-markdown-converter/main/INSTALL.md) and follow the path for your environment.

## Install | التثبيت

**Easiest | الأسهل:** give this repository's link to your AI tool and ask it to install the skill. It will read [INSTALL.md](INSTALL.md).
أعطِ رابط هذا المستودع لأداة الذكاء الاصطناعي التي تستخدمها واطلب منها تثبيت المهارة، وستتبع ملف INSTALL.md.

| Your tool | What to do |
|---|---|
| Claude Code | Ask it to install from this link, or copy `skills/lecture-to-markdown-converter/` to `~/.claude/skills/` |
| Claude.ai / ChatGPT skills | Upload the zip below in the app's skills settings. If its safety scan rejects code, use the zip without code |
| ChatGPT / Gemini / others | Add the single-file text to a custom GPT, Gem, project or custom instructions |
| Your own app / API | Use the single-file text as the system prompt |

- `lecture-to-markdown-converter`: [zip](https://raw.githubusercontent.com/nre-edu/lecture-to-markdown-converter/main/install/lecture-to-markdown-converter.zip) · [single file](https://raw.githubusercontent.com/nre-edu/lecture-to-markdown-converter/main/install/lecture-to-markdown-converter.md)
<!-- foundry:install:end -->


An AI skill that converts lecture and course files (PDF or slide decks, merged or separate) into a **complete, verbatim** Markdown reference, split by explicit tags so any LLM can retrieve a single lecture, plus a separate full-course mind map.

مهارة ذكاء اصطناعي تحوّل ملفات المحاضرات والمقررات (PDF أو عروض تقديمية، مجمّعة أو منفردة) إلى مرجع Markdown **حرفي وشامل** دون اختصار أو حذف، مقسّم بوسوم صريحة يسترجع بها أي نموذج لغوي محاضرة بعينها، مع ملف مستقل للخريطة الذهنية الشاملة للمقرر.

## What it does | ماذا تفعل

- Inspects every page and slide visually, not by OCR alone, and cross-checks a merged file against separate lecture files to catch missing lectures or slides.
- Transcribes text, pictured tables, diagrams and sample documents verbatim, flagging source typos instead of silently fixing them.
- Delivers **two files**: `محاضرات_<course>_كاملة.md` (navigation guide, index table, start/end tags per lecture, a marker per slide) and `الخريطة_الذهنية_لمحاضرات_<course>.md` (Mermaid `mindmap` + detailed tree).

- تفحص كل صفحة وشريحة بصريًا لا بنص OCR وحده، وتطابق الملف المجمّع بالملفات المنفردة لاكتشاف ما سقط.
- تفرّغ النصوص والجداول المصوّرة والمخططات والنماذج حرفيًا، وتشير إلى أخطاء المصدر بدل تصحيحها بصمت.
- تسلّم **ملفين**: ملف المحاضرات الكامل، وملف الخريطة الذهنية.

## Structure | الهيكل

```text
skills/lecture-to-markdown-converter/
├── SKILL.md                       # entry point (procedure and rules)
├── metadata.json                  # name, description, triggers, reference index
├── references/
│   ├── transcription-rules.md     # verbatim rules for text, tables, diagrams, forms
│   └── output-structure.md        # lectures file + mind-map file + Mermaid rules
└── tests/triggers.json            # trigger test prompts
INSTALL.md                         # install guide for AI agents (generated)
install/                           # zip, single-file text, Cursor rule (generated)
```

## Verification status | حالة التحقق

| Check | Status |
|---|---|
| Structure validated with [skill-foundry](https://github.com/nre-nec/skill-foundry) `validate --strict` | Passed (2026-10-24) |
| Ported from a Gemini-specific version: removed `allowed-tools: default_api google`, `google:show_file` and a fixed output path | Done (2026-10-24) |
| Trigger tests in `tests/triggers.json` run in a live environment | Not yet verified |
| Behaviour tested end-to-end on Claude Code / Claude.ai / ChatGPT / Gemini | Not yet verified |

## License
MIT. See [LICENSE](LICENSE).
