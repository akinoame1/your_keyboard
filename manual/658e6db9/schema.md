# The spec

Every setting, with its kind and limits. An answer uses only these keys; a key the keyboard does not have is refused by name, and a value outside its limits refuses the whole answer, saying where.

```text
schema: always 1; leave it out of an answer.
echo.placement: where the echo line sits — one of AboveKeys, BelowSymbols, BetweenRows1And2, BetweenRows2And3, BelowLetters, BelowKeyboard.
echo.chars: how many characters before the cursor the echo line shows — whole number 10..200.
echo.sizeSp: the echo line's text size — 10.0..48.0.
keys.labelSizeSp: the letters' size on the keys — 12.0..48.0.
keys.rowHeightDp: each row's height — 32.0..96.0.
keys.numberRow: a row of digits above the letters — true or false.
keys.symbolRow: the one-click symbol row above the letters — true or false.
keys.letterHints: print each letter's long-press symbol on its key — true or false.
keys.haptics: a buzz on each key — true or false.
keys.aimCorrection: correct presses toward where the thumb aims — true or false.
keys.bottomRow: the row under the letters, left to right — a list of 8 keys at most, each an object:
  key: "layer" (?123 / ABC), "space" or "enter" — exactly one of each in the row; or instead of key,
  type: the text a key types, one to four characters, shown on it.
  width: in key cells, a letter key being 1 — 0.5..8.0; by default layer and enter 1.5, space 5, a typing key 1.
  hold: optional, what holding it does — "switchKeyboard", "sendReport", "openSettings", or {"type": text} on a key that types, which replaces what its tap typed. Some key must keep "switchKeyboard": it is how the keyboard is left.
text.autoCapitalise: shift by itself at a sentence start — true or false.
text.autoSpace: a space after , . : ; ? ! and a spaced dash — true or false.
languages: the codes of the alphabets switched on, in the order a space-bar swipe walks them — a list of codes from alphabets, at least one.
alphabets: every alphabet the keyboard can type; each one is an object:
  code: a language code like en, he, ko or pt-BR, not used by another alphabet.
  label: one to four characters, shown on the space bar.
  name: what the settings screen calls it.
  rows: exactly three rows of keys, each row 1 to 13 keys, each key one to four characters.
  hasCase: whether there is a shift key — true or false.
  rightToLeft: whether the text runs right to left — true or false.
  align: where a short row's spare width goes — LEFT, CENTRED or RIGHT.
  rowAlign: optional, one alignment per row, overriding align — exactly three of LEFT, CENTRED, RIGHT.
  alternates: what a long press types — an object from a key of this alphabet to the text it types.
  longPressFromSymbols: take long presses from symbol page one instead of alternates, as Latin does — true or false.
  shifted: optional, what shift types instead of a capital — an object from a key of this alphabet to the text (Korean's ㅂ to ㅃ); with any entry, no capital is armed at a sentence start.
  composer: optional, the keyboard's composer that builds characters from several keys — only "hangul" exists (Korean two-set); leave it out for one key, one character.
symbols.oneClick: the one-click row's symbols, as one text, one symbol per character.
symbols.oneClickPerApp: one-click rows for particular apps — an object from an Android package name to its symbols.
symbols.pages: the symbol layer — a list of pages, each exactly three rows; a row holds at most 10, 9 and 7 symbols (the Latin letter rows), each one to four characters.
colours: the keyboard's colours, each one opaque, written #RRGGBB. Every text colour must have a contrast of at least 3 (WCAG 2) against what it is drawn on, or the answer is refused naming the pair: keyText on key, keyModifier, keyArmed, keyLocked; symbolText on key, keyModifier; hintText on key, echoBackground; echoAccent on echoBackground.
colours.background: behind the keys and in the gaps between them.
colours.key: a letter or symbol key's face.
colours.keyModifier: shift, backspace, ?123, enter, and the echo line's buttons.
colours.keyArmed: shift armed for one letter.
colours.keyLocked: shift locked on.
colours.keyText: a letter on its key, and a button's label.
colours.hintText: the small print — a long-press hint, the echo line's idle text.
colours.symbolText: every symbol and digit, wherever drawn.
colours.echoBackground: the echo line's strip.
colours.echoAccent: the text on the echo line, and the echo on the space bar.
```

## The default spec

What a keyboard nobody has changed holds. The message from a phone says only what differs from this.

```json
{
  "schema": 1,
  "echo": {
    "placement": "BelowSymbols",
    "chars": 60,
    "sizeSp": 22
  },
  "keys": {
    "labelSizeSp": 25,
    "rowHeightDp": 52,
    "numberRow": false,
    "symbolRow": true,
    "letterHints": false,
    "haptics": true,
    "aimCorrection": true,
    "bottomRow": [
      {
        "key": "layer",
        "width": 1.5,
        "hold": "sendReport"
      },
      {
        "type": ",",
        "width": 1,
        "hold": "switchKeyboard"
      },
      {
        "key": "space",
        "width": 5
      },
      {
        "type": ".",
        "width": 1
      },
      {
        "key": "enter",
        "width": 1.5
      }
    ]
  },
  "text": {
    "autoCapitalise": true,
    "autoSpace": true
  },
  "languages": ["en"],
  "alphabets": [
    {
      "code": "en",
      "label": "EN",
      "name": "English — qwerty",
      "rows": [["q", "w", "e", "r", "t", "y", "u", "i", "o", "p"], ["a", "s", "d", "f", "g", "h", "j", "k", "l"], ["z", "x", "c", "v", "b", "n", "m"]],
      "hasCase": true,
      "rightToLeft": false,
      "align": "CENTRED",
      "alternates": {},
      "longPressFromSymbols": true
    },
    {
      "code": "he",
      "label": "עב",
      "name": "עברית — the Israeli standard, right to left",
      "rows": [["'", "-", "ק", "ר", "א", "ט", "ו", "ן", "ם", "פ"], ["ש", "ד", "ג", "כ", "ע", "י", "ח", "ל", "ך", "ף"], ["ז", "ס", "ב", "ה", "נ", "מ", "צ", "ת", "ץ"]],
      "hasCase": false,
      "rightToLeft": true,
      "align": "RIGHT",
      "alternates": {
        "'": "1",
        "-": "2",
        "א": "5",
        "ו": "7",
        "ט": "6",
        "ם": "9",
        "ן": "8",
        "פ": "0",
        "ק": "3",
        "ר": "4"
      },
      "longPressFromSymbols": false
    },
    {
      "code": "ru",
      "label": "РУ",
      "name": "Русский — ЙЦУКЕН, ё on a long press of е",
      "rows": [["й", "ц", "у", "к", "е", "н", "г", "ш", "щ", "з", "х", "ъ"], ["ф", "ы", "в", "а", "п", "р", "о", "л", "д", "ж", "э"], ["я", "ч", "с", "м", "и", "т", "ь", "б", "ю"]],
      "hasCase": true,
      "rightToLeft": false,
      "align": "CENTRED",
      "alternates": {
        "е": "ё"
      },
      "longPressFromSymbols": false
    },
    {
      "code": "ko",
      "label": "한글",
      "name": "한국어 — two-set (dubeolsik), syllables built as you type",
      "rows": [["ㅂ", "ㅈ", "ㄷ", "ㄱ", "ㅅ", "ㅛ", "ㅕ", "ㅑ", "ㅐ", "ㅔ"], ["ㅁ", "ㄴ", "ㅇ", "ㄹ", "ㅎ", "ㅗ", "ㅓ", "ㅏ", "ㅣ"], ["ㅋ", "ㅌ", "ㅊ", "ㅍ", "ㅠ", "ㅜ", "ㅡ"]],
      "hasCase": true,
      "rightToLeft": false,
      "align": "CENTRED",
      "alternates": {},
      "longPressFromSymbols": false,
      "shifted": {
        "ㄱ": "ㄲ",
        "ㄷ": "ㄸ",
        "ㅂ": "ㅃ",
        "ㅅ": "ㅆ",
        "ㅈ": "ㅉ",
        "ㅐ": "ㅒ",
        "ㅔ": "ㅖ"
      },
      "composer": "hangul"
    }
  ],
  "symbols": {
    "oneClick": "-:;?()/#",
    "oneClickPerApp": {},
    "pages": [
      [["1", "2", "3", "4", "5", "6", "7", "8", "9", "0"], ["#", "-", "[", "]", "(", ")", ":", ";", "\""], ["?", "!", "'", "*", "_", "@", "/"]],
      [["%", "$", "+", "=", "&", "\\", "|", "^", "~", "`"], ["{", "}", "<", ">", "°", "₪", "€", "£", "•"], ["—", "…", "“", "”", "‘", "’", "×"]]
    ]
  },
  "colours": {
    "key": "#2C2C2F",
    "background": "#1B1B1D",
    "keyModifier": "#3B4256",
    "keyArmed": "#4E5E80",
    "keyLocked": "#6E8CC4",
    "keyText": "#F2F2F2",
    "hintText": "#9A9A9E",
    "symbolText": "#C3D0E8",
    "echoBackground": "#101012",
    "echoAccent": "#8AB4F8"
  }
}
```
