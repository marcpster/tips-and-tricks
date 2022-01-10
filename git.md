# git

## branch
### Create branch with uncommitted changes

  git checkout -b my_branch

## diff
### Diff files NOT in git

  git diff --no-index dl1 dl2

## log
### Use pretty format

  git log --pretty=format:"%h %an %ar: %s"

### Restrict folders ***-- f1 f2*** 

Restrict the log to specified folder(s). Note space after double dash.

`git log --oneline -- camdesktop2`

### Restrict date ***--since***

  `git log --oneline --since="2018-12-12T16:36:00-07:00"`

  `git log --oneline --since="0 weeks 0 days 20 hours 30 minutes 59 seconds ago"`

### Show file changes ***--stat***

   `git log --oneline --stat --since="1 hours"`