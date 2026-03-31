# Aura-Translations
This repository contains community-driven translations for Aura Video Downloader. Anyone can contribute a new language, improve existing localization, or help keep translations complete and up to date.

---

# How to Add a New Translation

Aura Video Downloader loads translations automatically from JSON files inside `aura/translations/`.

I will add new translations with every new update of the program.

## 1. Create a New Translation File

1. Copy the latest `en.json`.
2. Rename it to your language code.

Examples:
- `de.json` for German
- `fr.json` for French
- `pt-br.json` for Brazilian Portuguese
- `zh-cn.json` for Simplified Chinese

The filename, without `.json`, becomes the language code used by the app.

## 2. Use Valid JSON Only

Translation files must be valid JSON.

Important rules:
- Save the file as `UTF-8`
- Prefer `UTF-8 without BOM`
- Do not add comments
- Do not leave trailing commas
- Keep quotes escaped correctly, for example `\"`
- Keep newline escapes like `\n` when they are part of the original text

If the JSON is invalid, the app will not be able to load the translation.

## 3. Keep the Same Keys as `en.json`

The English file is the source of truth.

Rules:
- Do not remove keys
- Do not rename keys
- Do not invent your own replacement keys
- If you are unsure how to translate something, keep the English text for that key instead of deleting it

The safest workflow is:
1. Copy `en.json`
2. Translate only the values
3. Leave every key exactly as it is

## 4. Keep the Same Value Types

Do not change the data type of any value.

At the moment, translation files contain:
- mostly `string` values
- a small number of `list` values

Current list keys:
- `joke_welcome`
- `joke_finish`

Rules:
- if a value is a string in `en.json`, it must stay a string
- if a value is a list in `en.json`, it must stay a list
- do not convert a list into one long string
- do not convert a string into an object or array

## 5. Preserve All Placeholders Exactly

Many strings contain placeholders that are filled by the program at runtime.

Examples:
- `{platform}`
- `{path}`
- `{error}`
- `{n}`
- `{count}`
- `{name}`
- `{mode}`
- `{format}`
- `{current_year}`

Rules:
- keep the braces
- keep the placeholder name exactly the same
- do not translate placeholder names
- do not remove placeholders
- you may move placeholders inside the sentence if your language needs a different word order

Correct:
- `"Cookies: {n}"`
- `"Saved to: {path}"`

Incorrect:
- `"Cookies: {число}"`
- `"Saved to:"`
- `"Cookies: n"`

Special note:
- `{current_year}` is replaced automatically by the app
- this works both in normal strings and inside list items

## 6. Do Not Break Formatting

Some strings are used in logs, buttons, cards, menus, dialogs, and status messages.

Please preserve:
- leading spaces if they exist
- trailing spaces if they exist intentionally
- emoji markers
- punctuation
- line breaks
- path patterns
- file extensions
- technical fragments like `[id]`, `{format}`, `--playlist-items`, URL examples, language codes, browser names, and platform names when they should remain technical

Examples:
- `title [id].{format}` must keep `[id]` and `{format}`
- `en, es-419, ja` should keep the language codes
- `yt-dlp`, `FFmpeg`, `aria2c`, `YouTube`, `VK`, `TikTok` usually should not be translated as ordinary words

## 7. Add Optional Metadata for the Language Picker

The language selector supports optional metadata keys at the top of the file.

Recommended fields:
```json
{
  "_meta_language_name": "German",
  "_meta_language_native_name": "Deutsch",
  "_meta_language_tagline": "Full interface, hints, and system messages in German."
}
```

Meaning:
- `_meta_language_name`: language name in English
- `_meta_language_native_name`: language name in its own language
- `_meta_language_tagline`: short description shown in the language picker

Notes:
- keys starting with `_meta_` are service metadata
- they do not replace normal translation keys
- if metadata is missing, the app uses automatic fallback names when possible
- adding metadata is strongly recommended for a polished language card in the selector

## 8. Keep UI Text Reasonable in Length

Some strings are used in compact UI areas.

Please try to keep:
- button labels short
- menu labels short
- status chips compact
- long explanations only in descriptions, hints, and dialogs

A translation can be correct but still feel broken if every button becomes too wide.

## 9. Keep Tone Consistent

Try to match the meaning and tone of the original text:
- technical where the original is technical
- neutral where the original is neutral
- concise where the original is concise
- friendly where the original is friendly

Do not add new jokes, warnings, or legal claims that were not in the original text.

## 10. Automatic Discovery

New translation files are discovered automatically.

That means:
- if you add a valid new `*.json` file to `aura/translations/`
- and it has the correct structure
- it will appear in the language selector automatically

No manual registration in code should be required.

## 11. Final Checklist Before Submitting

Before opening a PR, make sure that:

- the file is valid JSON
- the file is encoded in UTF-8
- the filename is the correct language code
- all keys from `en.json` are present
- no extra random keys were added
- all placeholders like `{path}` and `{n}` are preserved
- list values are still lists
- metadata keys are filled in
- the translation was reviewed for overly long button labels and broken formatting

## 12. Recommended Rule

If you are unsure about any line:
- keep the original English text for that key
- do not delete the key
- do not guess the meaning if it may change the behavior or user expectation

A partially untranslated file is much safer than a broken one.

---
