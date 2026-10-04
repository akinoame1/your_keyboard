# Worked examples

Each request below has a shallow answer and a good one, and why. These were written by the keyboard's authors, not taken from real chats. Each answer has been put through the keyboard's own checks, and the outcome shown is what the keyboard does with it. Real answers will replace these as they come.

## "add Greek"

**A shallow answer.** The keyboard applies it.

```text
Here is a Greek alphabet.
{"alphabets": [{"code": "el", "label": "ΕΛ", "name": "Greek", "rows": ["αβγδεζηθι", "κλμνξοπρσ", "τυφχψως"], "hasCase": true}], "languages": ["en", "el"]}
```

**A good answer.** The keyboard applies it.

```text
Greek keyboards share one standard layout, so I used it: the letters where Greek hands expect them, with ; on the first key, where Greek's question mark sits on a physical keyboard. Accented vowels are on a long press of their vowel. The diaeresis forms (ϊ, ϋ) are left out: a key has one long press, and the accent is the commoner one.
{"alphabets": [{"code": "el", "label": "ΕΛ", "name": "Ελληνικά — the Greek standard layout", "rows": [";ςερτυθιοπ", "ασδφγηξκλ", "ζχψωβνμ"], "hasCase": true, "alternates": {"α": "ά", "ε": "έ", "η": "ή", "ι": "ί", "ο": "ό", "υ": "ύ", "ω": "ώ"}}], "languages": ["en", "el"]}
```

**Why.** Both apply. The shallow one puts the letters in alphabetical order, which no Greek typist has ever learned, and leaves out every accent. The good one starts from the layout people of that language already type on, and puts what the rows cannot hold on long presses.

## "bigger keys"

**A shallow answer.** The keyboard applies it.

```text
Done.
{"keys": {"rowHeightDp": 96}}
```

**A good answer.** The keyboard applies it.

```text
Keys are already as wide as the screen allows, so bigger means taller. I raised the rows from 52 to 60 dp and the letters from 25 to 29 sp, so the letters fill the taller keys. That makes the keyboard about 40 dp taller, which still leaves room for the text being written.
{"keys": {"rowHeightDp": 60, "labelSizeSp": 29}}
```

**Why.** Both apply. The shallow one turns one number to its maximum: keys nearly twice as tall, letters as small as before, and a keyboard covering half the screen. The good one says what limits the change (width is already full), balances height and letter size, and says what it costs.

## "in Termux I type commands; give me | ~ / - $ > & * on the one-click row"

**A shallow answer.** The keyboard applies it.

```text
I changed the one-click row.
{"symbols": {"oneClick": "|~/-$>&*"}}
```

**A good answer.** The keyboard applies it.

```text
These are for one app, so I gave Termux its own one-click row and left the row every other app uses as it is.
{"symbols": {"oneClickPerApp": {"com.termux": "|~/-$>&*"}}}
```

**Why.** Both apply. The shallow one replaces the row in every app with a terminal's symbols. The good one uses the per-app row, keyed by the app's Android package name.

## "add German"

**A shallow answer.** The keyboard applies it.

```text
Here is German.
{"alphabets": [{"code": "de", "label": "DE", "name": "Deutsch", "rows": ["qwertyuiop", "asdfghjkl", "zxcvbnm"], "hasCase": true, "alternates": {"a": "ä", "o": "ö", "u": "ü", "s": "ß"}}], "languages": ["en", "de"]}
```

**A good answer.** A question; nothing is applied until it is answered.

```text
Two layouts are in common use, and the choice changes every answer: German keyboards are QWERTZ (Z and Y swapped, with ü, ö and ä on keys of their own), but many people who also type English keep QWERTY with the umlauts on a long press. Which do you want?
```

**Why.** The shallow one chose for the person without saying there was a choice. When the answer depends on something only they know, ask first, and stop: no JSON until they have answered.

## "use a rounded font"

**A shallow answer.** The keyboard refuses it.

```text
Switching to a rounded font.
{"keys": {"font": "rounded"}}
```

**A good answer.** {}: the keyboard has no setting for this.

```text
The keyboard has no font setting: its letters are drawn in the phone's own font. It would need a setting naming a font, and the font shipped with the keyboard.
{}
```

**Why.** The shallow one invents a key; the keyboard refuses it by name and nothing changes. When no key in the schema can do it, answer {} and say what would be needed: that is what gets built next.

## "put a question mark next to the full stop"

**A shallow answer.** The keyboard refuses it.

```text
Added a ? key.
{"keys": {"bottomRow": [{"type": "?"}]}}
```

**A good answer.** The keyboard applies it.

```text
A list is replaced whole, so this is the whole bottom row: today's, with a ? key after the full stop. Holding it types ! instead, since the two go together. To make room, the space bar is 4 key cells instead of 5. The comma still holds the keyboard switcher.
{"keys": {"bottomRow": [{"key": "layer", "width": 1.5, "hold": "sendReport"}, {"type": ",", "width": 1, "hold": "switchKeyboard"}, {"key": "space", "width": 4}, {"type": ".", "width": 1}, {"type": "?", "width": 1, "hold": {"type": "!"}}, {"key": "enter", "width": 1.5}]}}
```

**Why.** The shallow one gives a list holding only the new key. A list is replaced whole, so that would be a row with no space bar or enter, and the keyboard refuses it. The good one writes out the whole row and keeps the way to switch keyboard.
