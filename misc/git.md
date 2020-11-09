# git

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