# Trunk-Based Development


The practice of committing to the main trunk (often referred to as "main" or "master") frequently or merging feature branches into main quickly is aligned with principles of Continuous Integration (CI) and Continuous Delivery (CD). It's commonly referred to as "Trunk-Based Development" or "Mainline Development."

1. Frequent Commits to Main:

	Developers commit their code changes directly to the main branch multiple times a day. These commits are typically small and self-contained. This practice ensures that changes are continuously integrated into the main codebase.

1. Feature Branches for Larger Work:

	For larger features or changes that may take more time to complete, developers create feature branches. These branches are still integrated into the main branch frequently, preferably daily.

1. Code Reviews:

	Code reviews are a critical part of the process. They should happen continuously as code is being committed to the main branch or feature branches. Code reviews in this context are often lightweight, focusing on smaller, more manageable changes.

	Continuous code reviews help catch issues early and ensure that code quality and standards are maintained.

1. Automated Testing:

	Continuous Integration (CI) practices are essential. Automated tests are run on every commit to the main branch, ensuring that new code doesn't introduce regressions. This also helps maintain a high level of code quality.

1. Feature Flags:

	In cases where a feature is not yet complete but needs to be merged into the main branch, feature flags can be used. Feature flags allow you to hide incomplete or experimental features until they are ready for release.

1. Release Planning:

	Release planning should be well-organized. Teams should have a clear understanding of what changes are ready for production and what might still be in progress. This is where feature flags can be handy, as you can release features independently.

1. Rollbacks:

	With frequent commits to main, it's crucial to be prepared for rollbacks in case an issue is discovered post-deployment. This means having a well-tested rollback plan and potentially automating the rollback process.

1. Monitoring and Feedback:

	Continuous monitoring of the application in production is vital. It allows for quick identification and resolution of issues. Feedback from users and automated error tracking can be valuable for identifying problems early.

1. Documentation:

	Thorough documentation of changes and releases is essential for keeping everyone informed about what has been deployed and what features are available.


## Workflow

Bill and Charlie are working on their local master branches.

1. Bill makes a change, commits and pushes to the remote master branch

	```
	# Bill's workflow
	$ git add .
	$ git commit -m "Make a change"
	$ git push origin master
	```
	
1. Charlie rebases his local master against the origin master.

	This updates his local master with the most recent commits made by bill. Charlie's local changes are reapplied on top of Billl's changes, creating a linear commit.

	```
	# Charlie's workflow
	$ git pull —rebase origin master
	```
	
1. Charlie reviews the changes, providing feedback and making suggestions.


Alternatively, if Charlie wants to address an issue or make a fix in the remote master branch:

1. Charlie stashes his local changes to save them temporarily before pulling Bill's commits.

	```
	$ git stash save "Temporary work"
	```
	
1. Charlie pulls the latest changes from the remote master branch to work on a fix. If there are no local changes to worry about, he can skip the stash step.

	```
	$ git pull origin master
	```
	
2. Charlie reviews the changes, makes fixes if necessary, and commits the fix.

	```
	# Code review, make fixes, and commit
	```
	
4. Charlie pushes the fix to the remote master branch.

	```
	$ git push origin master
	```

5. Charlie applies the stash to reapply his temporarily saved local changes.

	```
	$ git stash apply
	```

This workflow allows Charlie to address the issue in the remote master branch while temporarily stashing his local changes and then reapplying them after the fix is completed. It ensures that his work is not lost and that he can quickly switch context to resolve critical issues in the shared codebase.


## Feature Branches

Feature branches are short-lived and should ideally last only a day or a short duration. If a feature cannot be completed within this timeframe, it is often broken down into smaller, more manageable pieces.

### Workflow

1. Create and work on feature branch
1. Continuous Integration (CI) and testing

	Automated tests, including unit tests and integration tests, are run on the feature branch to ensure that it's in a deployable state.
1. Daily (or Frequent) Integration:

	At the end of the day or when the feature is ready, developers merge the feature branch into the main branch. Use merge to create merge commits, preserving the history of when each feature was integrated into the main branch.

	```
	# While on the feature branch (e.g., feature/my-feature)
	
	$ git checkout master  # Checkout the master branch
	$ git merge feature/my-feature  # Merge the feature branch into master
	$ git commit -m "Merge feature/my-feature into master"  # Commit the merge (if necessary)
	$ git push origin master  # Push the changes to the remote master branch
	```

1. Continuous Deployment (CD)

	The main branch, which receives frequent feature merges, is continuously deployed to production or a staging environment.

The process is repeated for each feature or task, ensuring that changes are continuously integrated into the main branch.