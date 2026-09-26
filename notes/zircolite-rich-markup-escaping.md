PR #154. A DFIR tool prints evidence file names into a Rich console. A file
named "[bold]x.evtx" had its name swallowed as markup; "a[/]b" as a directory
name could raise MarkupError out of a log call and end the run.

Fix: a safe_markup() helper (strip control chars, then rich.markup.escape),
applied at make_file_link and the raw-path log lines. rich.escape only escapes
the OPENING bracket — which is enough to neutralize a tag — and knowing that
saved a debugging spiral in the test assertions.
