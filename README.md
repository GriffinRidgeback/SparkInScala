# SparkInScala
This repository contains a skeleton project for creating Spark applications in the Scala IDE.

# Useful links for setup
Mostly, I followed this [article](http://docs.scala-lang.org/tutorials/scala-with-maven.html).

I needed some help from [here](http://stackoverflow.com/questions/35016945/scalac-error-bad-option-maketransitive-on-mvn-package-via-command-line) to resolve an initial build issue.

[This](https://www.mkyong.com/maven/how-to-configure-m2_repo-variable-in-eclipse-ide/) article shows how to correctly specify the workspace location for the eclipse goals.

# Extra steps (may not be needed but here just in case)
1. Have to add the Scala nature to the project
2. Have to make it a Maven project
3. Have to add [this](http://scala-ide.org/docs/tutorials/m2eclipse/) to the Eclipse environment

# Basic workflow
What works:
* download externally to ~/Development/SparkInScala
* needed to do this because modifications to .classpath and .project got lost and had to be re-done
* once those were fixed, did an import of Git projects, pointed to the ~/Development/SparkInScala directory
* git push, etc., work fine from Team menu item
* issue is synchronizing this README.md, as it is outside of the directory structure for the project.  Probably have to do command-line git pull/git pushh to keep it synchronized and avoid problems within the IDE when trying to push to an out-of-synch repository

How it __should__ work, now that the eclipse files have been fixed and pushed:
* Create the workspace
* Import from a clone URI
* fix the nature of the project and all should be fine

# Building the code
For now, what suffices is this:
<pre>
Create a new run configuration by right-clicking the pom.xml and specifying "compile" as the goal
</pre>

## Problems
When creating this repository and then pushing to remote, I got a the following error:

```
! [rejected]        master -> master (non-fast-forward)
```

To solve it, I tried a __fetch__ and __pull__ but neither worked.  What did work was this:
```
[15:11] ~/Development/SparkScalaIDE (528) $ git push
To ssh://github.com/GriffinRidgeback/SparkScalaIDE.git
 ! [rejected]        master -> master (non-fast-forward)
error: failed to push some refs to 'ssh://git@github.com/GriffinRidgeback/SparkScalaIDE.git'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. Integrate the remote changes (e.g.
hint: 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
[15:11] ~/Development/SparkScalaIDE (529) $ git pull --rebase
First, rewinding head to replay your work on top of it...
Applying: Initial commit of template for creating Spark code in the Scala IDE.
[15:13] ~/Development/SparkScalaIDE (530) $ git status
On branch master
Your branch is ahead of 'origin/master' by 1 commit.
  (use "git push" to publish your local commits)
nothing to commit, working tree clean
[15:13] ~/Development/SparkScalaIDE (531) $ git push
Counting objects: 18, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (10/10), done.
Writing objects: 100% (18/18), 2.97 KiB | 0 bytes/s, done.
Total 18 (delta 0), reused 0 (delta 0)
To ssh://github.com/GriffinRidgeback/SparkScalaIDE.git
   b4f06ef..fd1efae  master -> master
```
