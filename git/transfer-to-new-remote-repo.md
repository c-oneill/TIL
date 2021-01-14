#### Transfer to a new remote repo

Date: 01/14/2021

Sometimes it's handy to take an existing local project with a remote repository and transfer it to a new remote repository -- preserving branches, tags, and commit history. (Ex: transferring school projects to my profiles).

I learned this from [Nik Sumeiko](https://gist.github.com/niksumeiko) [here](https://www.smashingmagazine.com/2014/05/moving-git-repository-new-server/).

1. Make sure your local copy is completely up-to-date with the current remote.
    * `git fetch origin`
    * use `git pull` or `git merge origin/branch-name` 

2. Make sure you actually have all branches.
    * `git branch -a` will lists out all branches local and remote
    * if missing: `git checkout -b missing-branch origin/missing-branch`

3. Create a new repository on github (or wherever).

4. Add a new remote to the existing repository.
    * `git remote add new-origin https://github.com/user/new-remote-repo`

5. Push all branches to the new origin.
    * `git push --all new-origin` (maybe can use -u tag here?)
    * could also push each local branch separately: `git push -u new-origin remote-branch-name`
        * the `-u` tag will set up tracking

6. Push tags to the new origin.
    * `git push --tags new-origin`
    * tagging? --> [read here](https://git-scm.com/book/en/v2/Git-Basics-Tagging)

7. Remove the old origin.
    * `git remote rm origin`

8. Rename the new origin to fir conventions for the primary remote.
    * `git remote rename new-origin origin`