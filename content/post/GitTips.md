---
title: "Git Tips: pull, add, commit and push"
date: 2019-08-12T16:57:25+08:00
draft: false
tags: ["Git", "Tips"]
---

As a beginner, it is very often that I mess up my local or remote files with git and Github. Here are some tips that would be helpful for me and anyone who encountered the same problems.

## Clone (or Copy) remote file into your laptop

This one is the first step to do once you created a repository in github. To copy the repository from github, you need copy the link first and then do as following instructions
```python
# Example of cloning (or copying) file to your laptop from github
cd ~/Documents/...  # change directory (cd) to the file you want to save
git clone https://github.com/Michael-yunfei/DSGE.git  # paste the link of repository
```

## Add (or push) local files into github

Suppose, you created a new file called `MachineLearning.py`, you want to add or push it to github, then you should:
```python
cd ~/Documents/....  # change directory (cd) to the mirror file of github
# you have to change directory to the specific level that includes MachineLearning.py
git add MachineLearning.py
git commit -m "add machinelearning.py code"
git push
```

## Add (or push) all new created files

Suppose, you have created several files, and you can add them all to the github file

```python
cd ~/Documents/...  # change directory (cd) to the mirror file of github
git add .  # add all files
git commit -m "update the projects"  # sure, you can type whatever message you want
git push
```

## After commit, deleted some files and could not push?

Normally, one cannot push a single filer larger than 100 MB to github. Suppose you did not this at the beginning, and you did the `push` from the last step, and git returned error like this
```python
remote: Resolving deltas: 100% (3/3), completed with 2 local objects.
remote: error: GH001: Large files detected. You may want to try Git Large File Storage - https://git-lfs.github.com.
remote: error: Trace: 72300163a30ce81dd70ae95f036813e0
remote: error: See http://git.io/iEPt8g for more information.
remote: error: File Project/kin_dataset.csv is 384.99 MB; this exceeds GitHub's file size limit of 100.00 MB
To https://github.com/Michael-yunfei/MachineLearning.git
 ! [remote rejected]   master -> master (pre-receive hook declined)
error: failed to push some refs to 'https://github.com/Michael-yunfei/MachineLearning.git'
```

You realized that you could not push (or update) local files to github. To solve this problem, you can try:

```python
git status  # check the status first
```

This will tell you what you have done, and how many times you have done commit. For instance, if I have done 2 commits, and the following will be returned after `git status`:

```python
On branch master
Your branch is ahead of 'origin/master' by 2 commits.
  (use "git push" to publish your local commits)
```

Now, we need reset the commit by typing:

```python
git reset HEAD~2  # if you did 3 commits, change 2 to 3
# this step cleans all the actions you have done before
```

After this, you can check the status again by typing `git status`, then the follows will pop up:

```python
On branch master
Your branch is up to date with 'origin/master'.
# ....
# in the middle, it gives all the changes or created files you have done
# from the last git action.
# ....
no changes added to commit
```

Now, finally you can push again.

Let's say suppose that you messed up your local file, and you have also committed and pushed those changes to the master branch. If you want to get your repository back to the certain stage you are happy with. All you need to do is

* Go to your github and find the commit you want to get back to
* reset your local file and push it again

```python
git reset --hard <commit>
git push -f origin master  # -force, you can also do git push origin master
```

I found this [website](https://book.git-scm.com/book/en/v2) very useful. 
