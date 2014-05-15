git-101
=======

Git is a Version Control System similar to SVN and CVS. 
It has several advantages over other Version Control System that you can learn out there, but basically you get:

- Intuitive and flexible CLI.
- Managing multiple diverging branch is totally built-in and encouraged.
- Having separate Staging and Head areas makes the workflow much more flexible. Checkout this [nice docs][1] about them.

## Intro

This is a simple guideline of how to work with Git.
There's tons of tutorials and docs in the web so if you are new to Git you should
follow them in order to understand this properly:

- [Interactive Git tutorial in 15 minutes](https://try.github.io/levels/1/challenges/1)
- [Official Git Tutorial](http://git-scm.com/docs/gittutorial)
- [Extensive git interactive tutorial](http://gitimmersion.com/lab_01.html)
- [Atlassian Git tutorial](https://www.atlassian.com/git/tutorial)
- [Docs about Three Git trees: File System, Index and HEAD](http://git-scm.com/blog/2011/07/11/reset.html)


## Set up

After you install git you should run this one time configuration options:
```bash
git config --global user.name "Your Name Comes Here"
git config --global user.email you@yourdomain.example.com
```
## Basic workflow

In this section we will be reviewing step by step the basic workflow. Please review the official docs or the internet
for more detailed information.

- Download the repo and move to its directory.
```bash
git clone url repo
cd repo
```

> `repo` its just a variable, you can assign any name that you like or even leave it blank.


Lets say that you are working on adding some **Feature A** to you current code base.

- Create a new branch
 ```bash
git checkout -b feature_a
```

> `-b` is for creating a branch. `checkout` is for changing between branches. 
The main branch is called `master` by default.

- Suppose you need to edit the file `index.js`. Once you've done it you need to save those changes.
- Check status on the repository
```bash
git status
```
You'll see that `index.js` is modified.

- Add `index.js` to the **Index**
```bash
git add index.js
```
> If you run `git status` again you should see  the changes reflected.


- Commit or "Save" you files
```bash
git commit -m "Some message regarding the changes introduced. More details are better"
```
At this point you "Saved" your changes into your local repository. Most surely you'll want 
to "Upload" those changes into the remote repository, lets say Github.

- Push your changes into the remote repository
```bash
git push origin feature_a
```
> `origin` its just and alias for the remote repository url. Check it with `git remote -v`

> `feature_a` indicates that you want to push from that particular branch in your local repository
to that particular branch in the remote repository.

- Repeat!

Once your awesome **Feature A** is ready the you should move to merging and Pull Request section (next).

## Merging and Pull Requests

Once your branch `feature_a` is ready to be merged with `master` (the main code base) you should do the following.

- Make sure you latest changes are in the Remote Repository: `git add`,  `git commit`, `git pull origin feature_a`
- Make sure you have the latest change in `master` branch in your Local Repository

```bash
# Move to master branch
git checkout master
# Download latest changes
git pull origin master
```

- Merge!
```bash
# Move to feature_a branch
git checkout feature_a
# Merge master branch in your feature_a branch
git merge master
```

Git will attempt to merge it automatically.
This process may through **Merge Conflicts** that you'll need
to resolve manually and then run:
```bash
git add file1 file2 ...
git commit -m "merge with master"
```

The go to your Remote Repository web interface (Github, Bitbucket) and submit a Pull Request
from your `feature_a` branch into `master` branch and tell your partners, they will accept the Pull Request
and your code will be part of the `master` branch or main code base.

After that you should always remember to "Download" the latest changes in master with `git pull origin master`
and delete `feature_a` branch with `git branch -d feature_a` (this can be done through GitHub's web interface too).

## Frequency

- `git commit` should be done as frequent as you can do it. Maybe one for each time you change a file.
- `git push` should be done a few times a day or maybe only one.


Now you have a working

## Dictionary

- `master branch`: It refers to the main code base branch by default.
- `Local Repository`: when you work with git you always have a Local Repository. `git add`, `git commit`, etc, are all executed in the context of a Local Repository.
- `Remote Repository`: Most common are Github and Bitbucket but they are not the only out there. You should always save your latest changes into the Remote. Think of it as a Safe Zone for your code.
- `Index` or `Staging Area`: Part of Git Three Trees. When you run `git add file` you are moving `file` to the `Index`. Its just an intermediate Saving area.
- `HEAD`: Part of Git Three Trees. When you run `git commit -m "msg"`, you are moving all files in `Index` into `HEAD`. Files in `HEAD` are saved in your `Local Repository`.







[1]: http://git-scm.com/blog/2011/07/11/reset.html
