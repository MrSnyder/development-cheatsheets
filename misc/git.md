# git

## Default workflow: Edit, review, commit and push
```bash
# Compare working directory with repository state
git status
# Add single file to commit
git add filename
# Add all files in current directory (and below)
git add .
commit -m 'Message'
```

## Working with branches
```bash
# delete remote branch
git branch -D origin :branchname
# prune tracking branches not on the remote
git remote prune origin
```

## Working with the stash
```bash
# show stash
git stash show
# diff working directory file with stashed file
git diff stash@{1} -- <filename>
# restore single file from stash
git checkout stash@{0} -- <filename>
```

## Pulling / pushing
```bash
# fetch upstream origin and merge upstream/master into master
git pull upstream master
```

## Connect a local (non-git) repo to an existing remote repo
```bash
git init
# adapt the following line
git remote add origin git@github.com:yourname/projectname.git
git fetch
git branch master origin/master
git checkout master
```

## Storing passwords for remote repos (https)

https://www.softwaredeveloper.blog/git-credential-storage-libsecret

* Libsecret (GNOME)

```bash
sudo apt-get install libsecret-1-0 libsecret-1-dev
cd /usr/share/doc/git/contrib/credential/libsecret
sudo make
git config --global credential.helper /usr/share/doc/git/contrib/credential/libsecret/git-credential-libsecret
```

## Config

```bash
# show current config
git config --list
```

### Conditional config (e.g. different email addresses per path)

`~/.gitconfig`

```
[user]
	email = markus@beefcafe.de
	name = Markus Schneider
[color]
	ui = true
[core]
	editor = nano
[includeIf "gitdir:~/Development/01_projects/XYZ/"]
	path = ~/Development/01_projects/XYZ/etc/gitconfig
[credential]
	helper = store
```


`~/Development/01_projects/XYZ/etc/gitconfig`

```
[user]
	email = schneider@XYZ.de
```
