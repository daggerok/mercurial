# mercurial
Mergurial guide (for git users)

## commands

```bash
# setup user name settings `git config --global user.name "Maksim Kostromin"; git config --global user.email daggerok@gmail.com`
hg config --edit
# [ui]
# username = Maksim Kostormin <daggerok@gmail.com>

# init repo `git init`
hg init

# add files `git add .`
hg add .

# commit `git commit -am "message"`
hg commit -m "message"

# commit ignorring all log and tmp files
hg commit -X '**.log' -X '**.tmp'

# send update to remote repo `git push origin master`
hg push
hg push --branch default

# fetch changes from repo `git pull origin master`
hg pull

# merge dry run
hg merge -P

# merge curernt working directory with remove branch (pull must be used before merge to get changes from remote)
hg merge

# fetch (pull) changes and du update
hg pull -u

# remove files `git rm -rf some-file`
hg remove some-file

# remove files from stash `git rm -rf some-file --cached`
hg forget some-file

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
hg identify -b

# switch to another branch `git checkout feature`
hg update feature

# diff between revisions `git diff $hash1..$has2`
# hg diff -r $rev1 -r rev2
hg diff -r 127 -r 130
# hg status --rev $rev1:$rev2
hg status --rev 127:130
# when hg log shows something like:
#              $rev:$hash
# changeset:   3641:07dcw41efwe1

# revert files `git reset --hard $hash`
hg revert --all --rev 123
```

## configurations

**force mercurial do not ask password on Windows using TortoiseHg**

* install TortoiseHg, let say it into `C:\opt\TortoisHg` directory
* clone repo you want to not asked password anymore (replace my-user with yours)

```bash
hg clone ssh://hg@bitbucket.org/daggerok/rxjava-examples "C:\my-projects\rxjava-examples"
```

* edit `C:\my-projects\rxjava-examples\.hg\hgrc` file

```bash
notepad C:\my-projects\rxjava-examples\.hg\hgrc
```

* finally content of hgrc should be like so (replace my-password with yours)

```config
[paths]
default = ssh://hg@bitbucket.org/daggerok/rxjava-examples
[ui]
ssh = "C:\opt\TortoiseHg\lib\TortoisePlink.exe" -ssh -pw my-password
```

* verify that password is not prompting anymore

```bash
hg pull --cwd C:\my-projects\rxjava-examples
```

Done.
