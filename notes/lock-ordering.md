Pattern: a registry guarded by lock A, entries guarded by lock B. Eviction
wants to close an entry: take A, then B. Meanwhile the entry's own call holds
B for as long as the server takes to answer. Now every caller that needs A
waits on one stuck server. Global freeze from one slow upstream.

Fix shape: never close while holding the registry lock. Remove the entry
under A, close it after releasing. If the entry is busy, mark it doomed and
let the in-flight call close it in its finally. Regression test: one blocked
call must not delay a different key, and evicting an in-flight entry must not
delay its own key.
