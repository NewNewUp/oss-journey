PR #10406. PgVector upsert embedded ALL chunks before writing any. The write
phase had a batch_size guard; the embed phase didn't. A 1 MB spreadsheet ->
4,200 chunks -> every vector resident at once -> 512 MiB container OOM.

Fix: embed one batch, write it, release the vectors, repeat. The tricky part
was preserving the safety invariant: old content must stay retrievable until
the new content has actually landed. Solved with id bookkeeping instead of
eager embedding: read existing ids (strings, no vectors), roll back added ids
on failure, delete stale ids only after every batch landed.

Test lesson: my own test caught that written_ids was recorded before the
write succeeded — a failed batch's ids would have entered the rollback list.
