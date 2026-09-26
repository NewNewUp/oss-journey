After five PRs in 48 hours, GitHub started rejecting PR creation with
"does not have the correct permissions to execute CreatePullRequest" — a
secondary rate limit that looks like a permission error and isn't.

What worked: issue comments still worked when PR creation didn't (different
quota bucket). Diagnosis trick: try the same mutation in your OWN repo — if it
succeeds there, the block is repo-scoped, not account-scoped. And patience:
the window opens again.
