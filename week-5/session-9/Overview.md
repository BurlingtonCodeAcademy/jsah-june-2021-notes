# Tuesday 7/6/2021
Tonight we started by reviewing the Guess the Number project and walked through the initial set up and logic. We reviewed the main commands to save, add, commit, and push changes to GitHub. We wrapped up by talking about merge conflicts and how to manage them.

## Git & GitHub Review

<details>
<summary>Pulling down existing repository</summary>
<div>

1. Got to the existing repository.
2. Click the down arrow on the green `Code` button and select `HTTPS` or `SSH` link.
3. In your terminal, use the command below pasting the link you just copied in place of `[url]`.

    `$ git clone [url]`

</div>
</details>

<details>
<summary>Saving changes to Git and pushing to GitHub</summary>
<div>

1. **Save** you changes in VSCode:

2. **Add** the files you want to add to Git:

    * Either name the files you want to add.

	`$ git add nameOfFile.js`
    * Or add any changed files

	`$ git add .`

3. **Commit** your changes to take a snapshot of changes and persists them to Git folder:

      `$ git commit -m "description about what changes you're making"`

4. **Push** your changes to the linked repository in GitHub:

      `$ git push`


</div>
</details>

## Guess the Number Project
If you have not already, please sign up for the [Guess-the-Number](https://classroom.github.com/a/v1wJIBeC) project on GitHub. The project will be due Thursday, July 8th.

The [project description](https://online.burlingtoncodeacademy.com/lessons/project/guess-the-number) can be found here on the LMS.

<details>
<summary>Binary Search Demo</summary>
<div>

```js
Round-1
max: 20
min: 1
guess: 10
1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20
                   ^
Is your number 10? 
==> no
Is it higher or lower?
==> lower

Round-2
max: 9
min: 1
guess: 5
1 2 3 4 5 6 7 8 9
        ^
Is your number 5? 
==> no
Is it higher or lower?
==> lower

Round-3
max: 4
min: 1
guess: 2
1 2 3 4 

Is your number 2? 
==> no
Is it higher or lower?
==> higher

Round-4
max: 4
min: 3
guess: 3
3 4 

Is your number 3? 
==> yes
DONE!
```


</div>
</details>

## Reading & Homework

*IF* you have time after working on your project, start reading up on JavaScript arrays in preparation for our next class.
