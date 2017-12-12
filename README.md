# mercurial
Mergurial guide (for git users)

```bash
# setup user name settings `git config --global user.name "Maksim Kostromin"; git config --global user.email daggerok@gmail.com`
hg config --edit
# [ui]
# username = Maksim Kostormin <maksim.kostromin@jeppesen.com>

# init repo `git init`
hg init

# add files `git add .`
hg add .

# commit `git commit -am "message"`
hg commit -m "message"

# send update to remote repo `git push origin master`
hg push
hg push --branch default

# get updates from repo `git pull origin master`
hg pull
hg pull -u

# remove files `git rm -rf some-file`
hg remove some-file

# status `git status`
hg status

# history `git log`
hg log

# reset to branch `git reset --hard origin/master`
hg update default --clean

# show branches `git branch -a`
hg branches

# show current branch `git branch`
hg branch
```
