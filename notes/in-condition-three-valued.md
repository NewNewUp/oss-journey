Issue #8436. `uuid IN ?` with a positional array returned [] while the named
form worked. The interesting part of the report is the matrix: IN and
CONTAINSANY accept arrays in OPPOSITE styles, and the unsupported combination
fails silently — indistinguishable from "no rows".

Expected fix direction: make positional and named symmetric, and make the
unsupported combination raise instead of whispering an empty set.
