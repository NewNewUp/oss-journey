# When the review bot crashes, it is not a review failure

ArcadeDB runs a Claude reviewer on every PR. Its job crashed mid-run and marked the check red — an infra failure, not a finding. Distinguish bot-crashed from bot-disapproved before writing fixes: read the log for a verdict, not just the check color.
