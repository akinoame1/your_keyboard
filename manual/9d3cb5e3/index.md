# Prose keyboard: the manual

Edition 9d3cb5e3, published by akinoame1. Generated from the keyboard's code; an edition is never changed once published, and a keyboard whose spec changes links to a new one.

Prose is an Android keyboard for writing long prose. Everything a person may change about it is one JSON document, the spec. They change their keyboard by asking an AI chat: the AI answers with the part of the spec to change, and the keyboard's settings check that answer and show every change before anything is applied.

**Check word: cedar-saffron.** Write it on the first line of your answer, so the keyboard knows you read this manual.

## How to answer

1. If the request is open in a way that changes the answer (which rows, which alphabet, how big), ask your questions first, briefly, and stop: no JSON yet. If it is clear, answer at once.
2. Explain in a few sentences what the request touches, what you chose and why, and what you left out.
3. Where more than one answer is reasonable, give two or three alternatives of different ambition, each a short title line and its own JSON object; otherwise one. Nothing after the last.
4. An answer is ONE JSON object in the shape of the spec, holding only what changes. Objects merge key by key; "alphabets" merge by "code" (give the code and the changed fields; a new code adds a whole alphabet); "symbols.oneClickPerApp" merges by app, null removing one; any other list is replaced whole. Use only the schema's keys, within its limits; never invent a key: it is refused, with the whole answer. If none can do it, say so, answer {} and what would be needed; never an option that changes nothing.

## The pages

- [The layout](https://akinoame1.github.io/your_keyboard/manual/9d3cb5e3/layout.html): what is on the screen, top to bottom, and what cannot be changed yet.
- [Alphabets](https://akinoame1.github.io/your_keyboard/manual/9d3cb5e3/alphabets.html): what an alphabet is made of, how to add a language, and every default alphabet in full.
- [Typing helpers](https://akinoame1.github.io/your_keyboard/manual/9d3cb5e3/text-rules.html): what the keyboard does to the text by itself.
- [The spec](https://akinoame1.github.io/your_keyboard/manual/9d3cb5e3/schema.html): every setting, its limits, and the default spec in full.
- [Worked examples](https://akinoame1.github.io/your_keyboard/manual/9d3cb5e3/examples.html): requests with a shallow answer and a good one, and why.

The message from the person's phone says what differs there from the default spec. Your answer changes the spec on their phone: the default with those differences.
