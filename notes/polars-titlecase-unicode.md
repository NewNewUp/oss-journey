PR #29556. str.to_titlecase lowercased the whole string first, then uppercased
word starts. For Turkish-dotted İ (U+0130) the pre-pass expands it to i + U+0307
(combining dot) — an invisible character the input never had — and the dot is not
Alphabetic, so the next letter got capitalized mid-word: "İstanbul" -> "İ̇Stanbul".
For ß the pre-pass turned it into "ss" then "SS": "ß foo" -> "SS Foo" where Python
gives "Ss Foo".

Fix: never pre-lowercase. Word-start chars take char::to_titlecase() (Unicode
titlecase mapping, which knows ß -> "Ss"), the rest take to_lowercase(). Digit and
apostrophe boundaries unchanged ('a1b'.title() == 'A1B').

Lesson: Unicode case mapping is not round-trippable. Never assume lower(x).upper()
== x. Python and Rust both ship a separate titlecase mapping precisely for this.
