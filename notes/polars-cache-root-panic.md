Issue #29541. The cache-state pass iterates entries recorded by a first
traversal — but the first traversal only records caches with a parent. A
.cache() at the plan ROOT was never recorded, so its entry was empty, and the
second pass panicked on children.first().unwrap().

Fix: skip entries with no recorded cache nodes — restores pre-regression
behavior. Regression test discipline: assert the three panicking shapes from
the issue all collect to the uncached result.
