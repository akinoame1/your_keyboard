# The layout

Prose is a phone keyboard for writing long prose. Top to bottom:
- The echo line (echo): the text around the cursor, shown large. Tapping it moves the cursor; it can be dragged above or between the rows. At its right end (echo.buttons): undo, the field's send button, paste, and ⋮ for actions.
- Optional rows above the letters: digits (keys.numberRow) and one-click symbols (keys.symbolRow; symbols.oneClick, or symbols.oneClickPerApp).
- Three letter rows from the alphabet being typed (alphabets; the ones switched on are in languages). Every key is one width, the widest that fits; a short row's spare width goes where the alphabet's align says. The last letter row starts with shift, where there is one, and ends with backspace, in every alphabet.
- The bottom row (keys.bottomRow): by default ?123 (hold: send a report), comma (hold: switch keyboard), space, full stop, enter. A swipe across space changes alphabet.
- The symbol layer (symbols.pages) puts symbols in the letters' places on the Latin grid; the key in shift's place turns the page. Page one is also the Latin letters' long presses.

Not changeable yet: gestures beyond keys.letterGestures and keys.bottomRow, dragging rows by hand (only the echo line drags), key shapes and fonts. For those, answer {} and say what would be needed.
