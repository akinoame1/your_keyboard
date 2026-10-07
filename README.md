# your_keyboard

The public manual of **Prose**, an Android keyboard whose every setting — layout, alphabets,
symbol pages, sizes, typing helpers — is one JSON document that a person can change by asking an
AI chat.

The keyboard's message to the chat points at one folder here. Read its `index.md` first.

- `manual/<edition>/` — one edition of the manual. The folder's name is a hash of its pages; an
  edition is **never changed once published**, and a keyboard whose spec says something new links
  to a new folder. So a phone always reads the manual it was built with.

Every page is generated from the keyboard's code (`Manual.kt` in the keyboard's repository) and
published by a pull request; nothing here is edited by hand.

Current edition: [manual/70657cba/](manual/70657cba/index.html), the manual of the newest Prose keyboard.
