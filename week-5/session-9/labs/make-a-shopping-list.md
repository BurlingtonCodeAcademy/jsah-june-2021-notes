# Make a Shopping List

1. Inside your `shopping` directory, create a file named `groceries.txt`.

- You can use your editor by running `code .` (that's "code" then a space then a period)

2. Inside `groceries.txt` add the following lines:

```js
milk
eggs
chunky monkey ice cream
```

3. Go **back** to the command line and type the following commands:

    * `git status`
    * `git add .` _(that's "git Space add Space dot Enter")_
    * `git status`

Now look at the the two git status results. What is different between them? Why?

---

You should now see something like this:

```js
On branch master

Initial commit

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

    new file:   groceries.txt
```
> **Don't skim past the status message!** You won't understand it all yet, but get used to reading over console output and checking for anomalies.

This message is saying that there is one file with staged changes, and it's a file git has never seen before, and its name is `groceries.txt`. It's also trying to be helpful by telling you how to unstage this change if you want.

(But you *don't* want to do this now, so that message isn't actually very helpful, and in fact is adding to the confusing by cluttering the output.)

---

Now, commit your changes with the following command:
```js
git commit -m "shopping list"
```
You should see something like this:
```js
[master (root-commit) d8b9565] shopping list
 1 file changed, 3 insertions(+)
 create mode 100644 groceries.txt
 ```
Note that your *commit message* ("shopping list") is in the top line, and your file name ("groceries.txt") is in the bottom line.

Once again, run `git status`, expecting to see:
```js
On branch master
nothing to commit, working tree clean
```
And to prove that the change actually made it into the history, run git log.
```js
commit d8b95657eebea7083de1a4fb96ba7fb296637342
Author: Some Person <someone@burlingtoncodeacademy.com>
Date:   Fri Sep 1 12:00:00 2020 -0400

    shopping list
```
Again, **don't skim past this message**. Look for terms you understand. Try to figure out what the program is telling you. Is everything as you would expect? If not, what's different? What don't you understand?

---

## More Shopping

Let's pretend that you've gone shopping. You bought ice cream and milk, but the store was out of eggs. And when you got home you noticed you were out of ketchup.

1. Edit `groceries.txt` to contain only the following lines:

```js
eggs
ketchup
```
2. Go back to the **command line** and type the following command:
```js
git status
```
You should see:
```js
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

    modified:   groceries.txt

no changes added to commit (use "git add" and/or "git commit -a")
```
Again, git is *trying* to be helpful here, but mostly just adding parenthetical clutter. Try to figure out what it's *actually* telling you about the state of your filesystem. (Some answers are on the next slide.)

|message|	explanation|
|----|---|
|`On branch master`|	you are "on" the branch named "master" -- more about branches later|
|`Changes not staged for commit:`|	you have edited some files but haven't added or committed those changes yet|
|`modified: groceries.txt`|	there are some changes inside the file named `groceries.txt`|
|`no changes added to commit`	|you haven't staged any of these changes|

Finally, do the two-step:

```js
git add .
git status
git commit -m "oh no, out of condiments"
git status
```
It is a very good habit to run `git status` incessantly. Like, all the time, between every other git command.

---
## Shopping History

Now let's pretend that a few days have passed... (or a few hours...) and you ate all that ice cream and you want more.

But Ben & Jerry's has such weird ice cream names, and you can't remember whether you bought Chunky Monkey or Chubby Hubby or Cherry Garcia!

> It's an ice cream EMERGENCY!!!

Fortunately, git is a time machine. You can view any point in history and see the changes made at that point in history.

1. Use `git log` to show the history list
2. Find the commit id corresponding to the very first history entry
3. Use `git show` to show that entry
My commit id is `d8b9565` so I would run
```js
git show d8b9565
```
`git show` reveals a lot of information about a single commit, including:

* metadata (like the id and date and author and message)
* *changes* (in the *unix diff* format, illustrated below)

```js
commit d8b95657eebea7083de1a4fb96ba7fb296637342
Author: Some Person <someone@burlingtoncodeacademy.com>
Date:   Fri Sep 1 12:00:00 2020 -0400

    shopping list

diff --git a/groceries.txt b/groceries.txt
new file mode 100644
index 0000000..9f0ab0a
--- /dev/null
+++ b/groceries.txt
@@ -0,0 +1,3 @@
+milk
+eggs
+chunky monkey ice cream
```