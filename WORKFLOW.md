Git Rescue Lab - Workflow
Task 1: Bisect Finding
Bad Commit Hash: c99fb4209e6fb6e5ed2789893fdb2f893d61d6c6 (c99fb42)
Explanation: The bug was an off-by-one error in the BULK20 discount condition. The commit changed the comparison from items.length >= 5 to items.length > 5, which incorrectly excluded orders of exactly 5 items from receiving the 20% bulk discount.
Task 2: Commit Message Cleanup

The commit originally labeled "asdf" (c99fb42) was reworded via git rebase -i to "Fix off-by-one bug in BULK20 discount threshold" so the history actually reflects what the change did.

Task 3: Feature Merge

Merged feature/holiday-sale into main, resolving the conflict in pricing.js so all three discount codes (SAVE10, BULK20, HOLIDAY25) work independently and correctly, with the BULK20 off-by-one bug fixed as part of the resolution (>= restored). node test.js passes all four tests.

Task 4: Secret Removal

Found .env tracked in history, ran git rm --cached .env to stop tracking it going forward, and added a .gitignore containing .env so it can't be re-committed by accident.

Task 5: Release Tag

Tagged the final working commit as v1.0 once all tests passed.

Task 6: Workflow Questions

1. Branching Strategy Recommendation

GitHub Flow is my pick for a four-person team. It's lightweight, keeps main always deployable, and its short-lived feature branches sidestep the tangled merges that come with letting branches live too long — a good fit for a small team that needs to move quickly.

2. Removing the Secret from History

Fully erasing .env from every past commit would require a history-rewriting tool such as git filter-repo (or the older git filter-branch), followed by a force-push and having every collaborator re-clone. The assignment skipped this step because it's a heavy-handed operation — it rewrites the whole repo's history, and if the team isn't perfectly synced on the change, it can break everyone else's local copies. It's also worth noting the .env here only held fake sample credentials, so there was nothing real to protect by going that far for this exercise.

3. Rewriting History

Rewriting the "asdf" commit in Task 2 was fine because it existed only on my machine — no one else's work depended on it. Doing the same to a commit teammates had already pulled would be a problem: since a rewrite always produces a new commit hash, anyone still holding the old hash would end up with a timeline that's diverged from yours, leading to confusing conflicts when they try to sync back up.
