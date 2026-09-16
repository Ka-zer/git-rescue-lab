# Git Rescue Lab - Workflow
 
## Task 1: Bisect Finding
* **Bad Commit Hash:** c99fb42
* **Explanation:** The bug was caused because the code was checking the length of the items array (number of distinct products) instead of calculating the total quantity of items in the cart.
 
## Task 6: Workflow Questions
 
**1. Branching Strategy Recommendation**
For a small team of 4, I recommend GitHub Flow. I chose this because it is simple, keeps the main branch deployable, and avoids "merge hell" by encouraging short-lived feature branches, which is perfect for a small, fast-moving team.
 
**2. Removing the Secret from History**
To completely erase the `.env` file from all past commits, we would need to use a tool like `git filter-repo` or the older `git filter-branch`. This assignment didn't require that step because it aggressively rewrites the entire repository history, which is dangerous and can break the repository for other teammates if not coordinated perfectly.
 
**3. Rewriting History**
It was acceptable to rewrite history in Task 2 because the "asdf" commit was only on my local machine. It would NOT be acceptable to rewrite a commit my teammates had already pulled because changing a commit creates a brand new hash. If teammates already have the old hash, pushing the new one creates divergent timelines and massive merge conflicts.
 