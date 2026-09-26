A regression test that has only ever passed proves nothing about the bug it
guards. Before shipping the lock-ordering fix, I checked out the pre-fix
commit and ran the new concurrency tests against it: both failed exactly as
the issue predicted. Then and only then did the green run mean anything.

The same discipline caught a reviewer's wrong claim: their repro "crashed"
on code I could show passing. Evidence beats authority, including when the
authority is reviewing you.
