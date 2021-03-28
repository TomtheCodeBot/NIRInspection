# Contribution guidelines

## Name conventions for implementing tasks
- LOGIC-X: documentation for workflow, data structures for the application 
- DEV-X: implementation of the according logic
- BUG-X: patches for resolve errors during the development
- chore: environment change, clean up, delete unused code
- fix: hot fix after merging a PR
- doc: documentation related tasks

## Project workflow
### First time:
- Setup SSH
- Clone
- Set upstream points to HBRS-SDP/anomaly_detection_evaluation
### Normal day:
- Checkout `develop` branch. The stable development reside here. This step is important because you need to pull to this branch and also create other branches based on this branch.
```
git checkout develop
```
- Pull rebase (**Always do this before starting your own new branch**)
```
git pull --rebase upstream develop
```
- If you starts on some task: Create your branch of choice (for example, `mybranch`)
```
git checkout -b mybranch
```
- If you already created it
```
git checkout mybranch
```
- Pull rebase again just in case
```
git pull --rebase upstream develop
```
- Develop, add and commit on `mybranch`
- Pull rebase again before push (because someone might change the upstream when you were coding)
```
git pull --rebase upstream develop
```
- After that, push to origin
```
git push origin mybranch
```
- On your own repo or HBRS repo create a pull request 
  - **IMPORTANT** check the branches that are merging together. Make sure the branch being merged to is HBRS...**develop** (on the left of the `<-` arrow) and the branch to merge is the branch from your repo `your_repo...mybranch` (on the right of the arrow).
  - Remember to set appropriate parameters if applicable, for example: link issue, reviewer, milestone...)
- Check if your pull request appears on HBRS repo
- Wait for reviews, make changes if needed.
- If changes are requested, make them in you branch and push to origin as before.
- After the reviewers accept your change, you are ready to merge (**don't click the `Merge` button yet**)
- First you need to pull rebase again because someone might merge before you (**Always do this**)
```
git checkout mybranch
git pull --rebase upstream develop
git push origin mybranch
```
- If someone **did** merge before you, then push to your origin will likely fail, so you need to force push
```
git push -f origin mybranch
```
- Then go to your pull request in the HBRS repo, change the green `Merge` button to `Squash and merge` and click on it.
- After merging is complete, update develop branch on your own repo
```
git checkout develop
git pull --rebase upstream develop
git push origin develop
```
- You can then delete your branch \
**IMPORTANT**: Don't delete if your branch is the `develop` branch.
```
git branch -d mybranch
git push --delete origin mybranch
```
