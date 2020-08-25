# Grading and submission

## Local tests and grading

Each lab is shipped with two sets of tests:
  * The tests defined under `src/test/scala`, these are usually incomplete: we
    strongly encourage you to write additional tests to exercise every aspect of
    your code. You can run these tests from `sbt` using the following command:
    ```shell
    test
    ```
  * The **grading tests**, that we use to grade your labs, these are
    provided as a "black box": you can run them but are not allowed to see their
    content, to encourage you to write your own tests. You can run them from
    `sbt` using the following command:
    ```shell
    runGradingTests
    ```
    **[Note: this command is currently broken on Windows, click here for the
    fix](https://gitlab.epfl.ch/lamp/cs210-2020/issues/9#note_45529)**

    Your grade is determined by the number of these tests that pass, see the
    next section to see how to actually get a grade.

(remember that you can always put `~` before an sbt command to automatically
re-run it when you save a file)

## Committing and pushing your code

**You need to push your code to gitlab to receive a grade. If you forget, your
grade will be zero.**

If you've read the first few chapters of [Git
book](https://git-scm.com/book/en/v2) as recommended, you must already be
familiar with committing and pushing, but let's go over the basics once again:

At any point while working on an lab, you can see what changes you
haven't committed by writing:
```shell
git status
```

(If you get the error `Not a valid command: git`, it means you're inside sbt,
you can't run git from sbt itself, you need to open another terminal in the same
directory)

This will display the list of files you have modified since the last commit, to
see the exact changes you made, run:
```shell
git diff
```

To save these changes in a commit, run: (replace `"My message"` by a message
describing the changes since the last commit, see [How to Write a Git Commit
Message](https://chris.beams.io/posts/git-commit/) for some tips on writing
good commit messages)
```shell
git commit -am "My message"
```

(It's good practice to commit your code regularly to document your changes)

You can then synchronize your local git repository with the gitlab server by
first running:
```shell
 git pull
```

This will merge in your local repository any change we made to the lab
(we only change labs to fix critical bugs found after it's been released,
so most of the time this will not do anything).

Finally, you can push your changes to gitlab:
```shell
git push
```

Note that there are also graphical user interfaces to interact with git, for
example [VSCode has built-in git
support](https://code.visualstudio.com/docs/editor/versioncontrol#_git-support).

Once you've pushed your code, you can see the result online by going to
`gitlab.epfl.ch/lamp/student-repositories-f20/cs210-GASPAR/pipelines` where
`GASPAR` is your username (you can also access this page from the main page of
your repository by clicking on the rocket icon on the left side of the gitlab
interface, then clicking on "Pipelines").

![](images/pipeline-tab.png)

The grading pipeline contains two steps:
  * *compile*: your code does not compile for grading if the job fail.
  * *grade*: the job results in a warning if you do not get the maximum grade
    (10.00/10.00)

You can click on the jobs to see the logs:

![](images/pipeline-details.png)

![](images/pipeline-logs.png)

Your grade is given on the line that starts with `Your overall score for this
lab is`

**If you push to gitlab multiple times, your final grade will be based on the
last commit you pushed before the deadline.**

## Troubleshooting

### Wrong remote address

```
Cloning into 'cs206-example'...
GitLab: The project you were looking for could not be found.
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.
```

If you get the above message, you ever used the wrong clone URL or you recently created your account on gitlab.epfl.ch, please wait 15 minutes and try again.
