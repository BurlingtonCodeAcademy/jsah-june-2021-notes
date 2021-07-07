# Create a Repo

Open up your terminal, `cd code`, and type the following commands in order:

| command        | explanation                                                        |
| -------------- | ------------------------------------------------------------------ |
| `mkdir shopping` | makes a directory named `shopping` (inside the directory named `code`) |
| `cd shopping`   | change the *current directory* to the new `shopping` directory         |
| `git init`      | bless the current directory as a git repo                          |
| `git status`     | show the state of the current repo                                 |

You should see something like this:
```js
$ git init
Initialized empty Git repository in /Users/Someone/code/shopping/.git/

$ git status
On branch master

Initial commit

nothing to commit
```