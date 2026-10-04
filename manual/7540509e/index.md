# Prose keyboard: the manual

Edition 7540509e. Generated from the keyboard's code; an edition is never changed once published, and a keyboard whose spec changes links to a new one.

Prose is an Android keyboard for writing long prose. Everything a person may change about it is one JSON document, the spec. They change their keyboard by asking an AI chat: the AI answers with the part of the spec to change, and the keyboard's settings check that answer and show every change before anything is applied.

**Check word: nectar-yarrow.** Write it on the first line of your answer, so the keyboard knows you read this manual.

## How to answer

1. If the request is open in a way that changes the answer (which rows, which alphabet, how big), ask your questions first, briefly, and stop: no JSON yet. If it is clear, answer at once.
2. Explain in a few sentences what the request touches, what you chose and why, and what you left out.
3. Where more than one answer is reasonable, give two or three alternatives of different ambition, from the smallest change that does it to a fuller one: each on a line with a short title, then its own JSON object. Otherwise give one.
4. Each answer is ONE JSON object in the shape of the spec, holding only what changes; nothing after the last. Objects merge key by key; "alphabets" merge by "code" (give the code and the changed fields; a new code adds a whole alphabet); "symbols.oneClickPerApp" merges by app, null removing one; any other list is replaced whole. Use only the keys in the schema, within its limits. If none can do it, answer {} and say what would be needed.

## The pages

- [The layout](https://raw.githubusercontent.com/akinoame1/your_keyboard/main/manual/7540509e/layout.md): what is on the screen, top to bottom, and what cannot be changed yet.
- [Alphabets](https://raw.githubusercontent.com/akinoame1/your_keyboard/main/manual/7540509e/alphabets.md): what an alphabet is made of, how to add a language, and every default alphabet in full.
- [Typing helpers](https://raw.githubusercontent.com/akinoame1/your_keyboard/main/manual/7540509e/text-rules.md): what the keyboard does to the text by itself.
- [The spec](https://raw.githubusercontent.com/akinoame1/your_keyboard/main/manual/7540509e/schema.md): every setting, its limits, and the default spec in full.
- [Worked examples](https://raw.githubusercontent.com/akinoame1/your_keyboard/main/manual/7540509e/examples.md): requests with a shallow answer and a good one, and why.

The message from the person's phone says what differs there from the default spec. Your answer changes the spec on their phone: the default with those differences.
