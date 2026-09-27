# One trim to match int() across every base

to_integer used num_traits from_str_radix, which rejects whitespace where Python int() accepts it. The fix was one trim call before parse — but the interesting part was the tell: +1 already parsed (sign tolerated), so only whitespace was missing. Asymmetry reports usually point at the exact missing line.
