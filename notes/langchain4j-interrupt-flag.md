PR #6483. Two catch blocks swallowed InterruptedException without restoring
the thread's interrupt flag. In Java, catching InterruptedException CLEARS the
flag; the contract requires Thread.currentThread().interrupt() if you re-throw
or handle it. Without it, cancellation requests vanish: K8s graceful shutdown
asks the thread to stop, the flag is gone, the pool reuses the thread, nobody
ever knows.

Fix: +5 lines. Same class of bug was being swept across the whole repo (#6481,
#6473) — joining a sweep is a legitimate, merge-fast contribution pattern.
