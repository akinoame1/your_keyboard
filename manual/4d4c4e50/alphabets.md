# Alphabets

Each alphabet is one object in the spec's "alphabets" list. The ones a person types in are switched on by their code in "languages", in the order a swipe across the space bar walks them. An answer changes an alphabet by giving its code and only the fields that change; a new code adds a whole alphabet.

## What an alphabet is made of

- code: a language code (en, he, pt-BR), unique.
- label: 1 to 4 characters, shown on the space bar.
- name: its name in settings.
- rows: three rows of 1 to 13 keys; a row is a list of keys of 1 to 4 characters, or one string with a key per character.
- hasCase (true/false): has shift and capitals.
- rightToLeft (true/false): the text runs right to left.
- align: LEFT, CENTRED or RIGHT, where a short row's spare width goes.
- rowAlign: optional, three alignments, one per row, overriding align.
- alternates: what a long press types, {key: text}.
- longPressFromSymbols (true/false): take long presses from symbol page one instead, as Latin does.
- shifted: optional, what shift types instead of a capital, {key: text} (Korean ㅂ → ㅃ); with any entry, no capital at a sentence start.
- composer: optional, builds characters from several keys; only "hangul" (Korean two-set) exists.

## How to add a language

- Start from the layout people of that language already type on: their national keyboard, its letters in the rows and places they have there. Hands that know a layout expect each letter where it was; rearranging letters to fit a tidy grid spends that for nothing.
- Three rows, 1 to 13 keys each. Rows may differ in length: Hebrew is 10/10/9 and Russian 12/11/9, because that is where those letters are on those keyboards.
- Letters the rows cannot hold go on a long press of the letter they are closest to (alternates): accented forms on their base letter, a final form on its letter.
- The language's own punctuation, where it differs (Greek's question mark is ;), goes on a long press or in the one-click row (symbols.oneClick).
- hasCase when the script has capitals; rightToLeft for a script written right to left, usually with align RIGHT so every row ends on the edge the script reads from.
- A script that builds one character from several keys needs a composer. Only "hangul" (Korean two-set) exists; for any other (Japanese kana to kanji, Chinese pinyin, Vietnamese Telex), say so and answer {}.
- Switch it on: add its code to "languages". The label is what the space bar shows, one to four characters.
- When it is not clear which layout is meant (a language with more than one in common use), ask first.

## The default alphabets

### English — qwerty (en)

```json
{
  "code": "en",
  "label": "EN",
  "name": "English — qwerty",
  "rows": ["qwertyuiop", "asdfghjkl", "zxcvbnm"],
  "hasCase": true,
  "rightToLeft": false,
  "align": "CENTRED",
  "alternates": {},
  "longPressFromSymbols": true
}
```

### עברית — the Israeli standard, right to left (he)

```json
{
  "code": "he",
  "label": "עב",
  "name": "עברית — the Israeli standard, right to left",
  "rows": ["'-קראטוןםפ", "שדגכעיחלךף", "זסבהנמצתץ"],
  "hasCase": false,
  "rightToLeft": true,
  "align": "RIGHT",
  "alternates": {"'": "1", "-": "2", "א": "5", "ו": "7", "ט": "6", "ם": "9", "ן": "8", "פ": "0", "ק": "3", "ר": "4"},
  "longPressFromSymbols": false
}
```

### Русский — ЙЦУКЕН, ё on a long press of е (ru)

```json
{
  "code": "ru",
  "label": "РУ",
  "name": "Русский — ЙЦУКЕН, ё on a long press of е",
  "rows": ["йцукенгшщзхъ", "фывапролджэ", "ячсмитьбю"],
  "hasCase": true,
  "rightToLeft": false,
  "align": "CENTRED",
  "alternates": {"е": "ё"},
  "longPressFromSymbols": false
}
```

### 한국어 — two-set (dubeolsik), syllables built as you type (ko)

```json
{
  "code": "ko",
  "label": "한글",
  "name": "한국어 — two-set (dubeolsik), syllables built as you type",
  "rows": ["ㅂㅈㄷㄱㅅㅛㅕㅑㅐㅔ", "ㅁㄴㅇㄹㅎㅗㅓㅏㅣ", "ㅋㅌㅊㅍㅠㅜㅡ"],
  "hasCase": true,
  "rightToLeft": false,
  "align": "CENTRED",
  "alternates": {},
  "longPressFromSymbols": false,
  "shifted": {"ㄱ": "ㄲ", "ㄷ": "ㄸ", "ㅂ": "ㅃ", "ㅅ": "ㅆ", "ㅈ": "ㅉ", "ㅐ": "ㅒ", "ㅔ": "ㅖ"},
  "composer": "hangul"
}
```
