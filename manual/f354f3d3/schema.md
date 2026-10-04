# The spec

Every setting, with its kind and limits. An answer uses only these keys; a key the keyboard does not have is refused by name, and a value outside its limits refuses the whole answer, saying where.

```text
schema: always 1; leave it out of an answer.
echo.placement: AboveKeys, BelowSymbols, BetweenRows1And2, BetweenRows2And3, BelowLetters, BelowKeyboard.
echo.chars (10 to 200): characters shown before the cursor.
echo.sizeSp (10 to 48): the echo line's text size.
echo.buttons: the echo line's end buttons in order, each {"button": "undo"|"submit"|"paste"|"more", "width": 28 to 96 dp}; by default undo 34, submit as wide as its label, paste 52, more 34. "more" (⋮) must stay.
keys.labelSizeSp (12 to 48): the letters' size.
keys.rowHeightDp (32 to 96): each row's height.
keys.numberRow, keys.symbolRow (true/false): the digit row and the one-click row.
keys.rowOrder: the digit row, the one-click row, the letters and the bottom row, top to bottom, each once: "numbers", "symbols", "letters", "bottom". The echo line's slots follow the letters.
keys.letterHints (true/false): print each letter's long press on its key.
keys.haptics (true/false): a buzz on each key.
keys.aimCorrection (true/false): move presses to where the thumb aimed.
keys.letterGestures: what holding (hold) or swiping a letter (swipeUp, swipeDown, swipeLeft, swipeRight) types in place of it: "none", "alternate", "capital". Default: hold "alternate", swipes "none".
keys.bottomRow: the row under the letters, left to right, at most 8 keys. Each is {"key": "layer"} (?123), {"key": "space"} or {"key": "enter"}, exactly one of each, or {"type": text of 1 to 4 characters}, and may have:
  width (0.5 to 8 key cells): by default layer and enter 1.5, space 5, others 1.
  hold: "switchKeyboard", "sendReport", "openSettings", or {"type": text} on a key that types, replacing what its tap typed. Some key must keep "switchKeyboard".
text.autoCapitalise (true/false): shift by itself at a sentence start.
text.autoSpace (true/false): a space after , . : ; ? ! and a spaced dash.
languages: codes of the alphabets switched on, in swipe order; at least one.
alphabets: every alphabet the keyboard can type, each an object:
  code: a language code (en, he, pt-BR), unique.
  label: 1 to 4 characters, shown on the space bar.
  name: its name in settings.
  rows: three rows of 1 to 13 keys; a row is a list of keys of 1 to 4 characters, or one string with a key per character.
  hasCase (true/false): shift and capitals.
  rightToLeft (true/false).
  align: LEFT, CENTRED or RIGHT, where a short row's spare width goes.
  rowAlign: optional, three alignments, one per row, overriding align.
  alternates: what a long press types, {key: text}.
  longPressFromSymbols (true/false): take long presses from symbol page one instead, as Latin does.
  shifted: optional, what shift types instead of a capital, {key: text} (Korean ㅂ → ㅃ); with any entry, no capital at a sentence start.
  composer: optional, builds characters from several keys; only "hangul" (Korean two-set) exists.
symbols.oneClick: the one-click row, one symbol per character.
symbols.oneClickPerApp: {Android package: its one-click row}.
symbols.pages: the symbol layer, pages of three rows of at most 10, 9 and 7 symbols, written as alphabet rows are.
colours: #RRGGBB, opaque: background (behind keys), key (letter, symbol faces), keyModifier (shift, backspace, ?123, enter, echo buttons), keyArmed, keyLocked (shift armed, locked), keyText (letters, labels), hintText (small print), symbolText (symbols, digits), echoBackground, echoAccent (echo strip, text). Text needs contrast 3 (WCAG 2) on what it is drawn on: keyText on key, keyModifier, keyArmed, keyLocked; symbolText on key, keyModifier; hintText on key, echoBackground; echoAccent on echoBackground.
```

## The default spec

What a keyboard nobody has changed holds. The message from a phone says only what differs from this.

```json
{
  "schema": 1,
  "echo": {
    "placement": "BelowSymbols",
    "chars": 60,
    "sizeSp": 22,
    "buttons": [
      {"button": "undo", "width": 34},
      {"button": "submit"},
      {"button": "paste", "width": 52},
      {"button": "more", "width": 34}
    ]
  },
  "keys": {
    "labelSizeSp": 25,
    "rowHeightDp": 52,
    "numberRow": false,
    "symbolRow": true,
    "letterHints": false,
    "haptics": true,
    "aimCorrection": true,
    "rowOrder": ["numbers", "symbols", "letters", "bottom"],
    "letterGestures": {
      "hold": "alternate",
      "swipeUp": "none",
      "swipeDown": "none",
      "swipeLeft": "none",
      "swipeRight": "none"
    },
    "bottomRow": [
      {"key": "layer", "width": 1.5, "hold": "sendReport"},
      {"type": ",", "width": 1, "hold": "switchKeyboard"},
      {"key": "space", "width": 5},
      {"type": ".", "width": 1},
      {"key": "enter", "width": 1.5}
    ]
  },
  "text": {"autoCapitalise": true, "autoSpace": true},
  "languages": ["en"],
  "alphabets": [
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
    },
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
    },
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
    },
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
  ],
  "symbols": {
    "oneClick": "-:;?()/#",
    "oneClickPerApp": {},
    "pages": [
      ["1234567890", "#-[]():;\"", "?!'*_@/"],
      ["%$+=&\\|^~`", "{}<>°₪€£•", "—…“”‘’×"]
    ]
  },
  "colours": {
    "background": "#1B1B1D",
    "key": "#2C2C2F",
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
