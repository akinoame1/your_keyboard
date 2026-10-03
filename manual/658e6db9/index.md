# Prose keyboard: the manual

Edition 658e6db9. Generated from the keyboard's code; an edition is never changed once published, and a keyboard whose spec changes links to a new one.

Prose is an Android keyboard for writing long prose. Everything a person may change about it is one JSON document, the spec. They change their keyboard by asking an AI chat: the AI answers with the part of the spec to change, and the keyboard's settings check that answer and show every change before anything is applied.

**Check word: umber-dune.** Write it on the first line of your answer, so the keyboard knows you read this manual.

## How to answer

1. If the request is open in a way that changes the answer -- which rows, which alphabet, how big -- ask your questions first, briefly, and stop there: no JSON until the person has answered. If it is clear, answer at once.
2. Then explain in a few sentences what you considered: which parts of the keyboard the request touches, what you chose and why, and anything you chose not to do.
3. Last, ONE JSON object in the shape of the spec holding only what changes. Objects merge key by key; "alphabets" merge by "code" (give the code and only the fields that change; a new code adds a whole alphabet); "symbols.oneClickPerApp" merges by app, and null removes an app's row; any other list is replaced whole. Use only the keys in SCHEMA, within its limits. Nothing after the object. If the request cannot be done with these keys, the object is {} and your explanation says what would be needed.

## The pages

- [The layout](https://raw.githubusercontent.com/akinoame1/your_keyboard/main/manual/658e6db9/layout.md): what is on the screen, top to bottom, and what cannot be changed yet.
- [Alphabets](https://raw.githubusercontent.com/akinoame1/your_keyboard/main/manual/658e6db9/alphabets.md): what an alphabet is made of, how to add a language, and every default alphabet in full.
- [Typing helpers](https://raw.githubusercontent.com/akinoame1/your_keyboard/main/manual/658e6db9/text-rules.md): what the keyboard does to the text by itself.
- [The spec](https://raw.githubusercontent.com/akinoame1/your_keyboard/main/manual/658e6db9/schema.md): every setting, its limits, and the default spec in full.

The message from the person's phone says what differs there from the default spec. Your answer changes the spec on their phone: the default with those differences.
