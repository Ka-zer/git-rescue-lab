Task 1: Bisect Finding

Bad Commit Hash: c99fb42
Explanation: (recommend correcting to match the actual diff — see above)

Task 6: Workflow Questions

1. Branching Strategy Recommendation
GitHub Flow is my pick for a four-person team. It's lightweight, keeps main always deployable, and its short-lived feature branches sidestep the tangled merges that come with letting branches live too long — a good fit for a small team that needs to move quickly.

2. Removing the Secret from History
Fully erasing .env from every past commit would require a history-rewriting tool such as git filter-repo (or the older git filter-branch). The assignment skipped this step because it's a heavy-handed operation — it rewrites the whole repo's history, and if the team isn't perfectly synced on the change, it can break everyone else's local copies.

3. Rewriting History
Rewriting the "asdf" commit in Task 2 was fine because it existed only on my machine — no one else's work depended on it. Doing the same to a commit teammates had already pulled would be a problem: since a rewrite always produces a new commit hash, anyone still holding the old hash would end up with a timeline that's diverged from yours, leading to confusing conflicts when they try to sync back up.
