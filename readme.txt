git commands to resolve changes in two different branches

root@ip-172-31-33-113:/tmp# git clone https://github.com/maheshkharwadkar/starte                                                      r-web.git
Cloning into 'starter-web'...
remote: Enumerating objects: 39, done.
remote: Total 39 (delta 0), reused 0 (delta 0), pack-reused 39
Unpacking objects: 100% (39/39), done.
root@ip-172-31-33-113:/tmp# ls
hsperfdata_jenkins
hsperfdata_root
jetty-0.0.0.0-8080-war-_-any-7111822269523659538.dir
jna--1712433994
starter-web
systemd-private-2538dc77771142e5a5c10636841d118a-systemd-resolved.service-DUcnFR
systemd-private-2538dc77771142e5a5c10636841d118a-systemd-timesyncd.service-5flAF                                                      C
winstone7514615722735654848.jar
root@ip-172-31-33-113:/tmp# cd starter-web/
root@ip-172-31-33-113:/tmp/starter-web# ls
404.html                          crossdomain.xml  fonts       js
README.md                         css              humans.txt  robots.txt
apple-touch-icon-precomposed.png  favicon.ico      index.html  simple.html
root@ip-172-31-33-113:/tmp/starter-web# git status
On branch master
Your branch is up to date with 'origin/master'.

nothing to commit, working tree clean
root@ip-172-31-33-113:/tmp/starter-web# git status
On branch master
Your branch is up to date with 'origin/master'.

nothing to commit, working tree clean
root@ip-172-31-33-113:/tmp/starter-web# git checkout -b myfeature_monu
Switched to a new branch 'myfeature_monu'
root@ip-172-31-33-113:/tmp/starter-web# ls
404.html                          crossdomain.xml  fonts       js
README.md                         css              humans.txt  robots.txt
apple-touch-icon-precomposed.png  favicon.ico      index.html  simple.html
root@ip-172-31-33-113:/tmp/starter-web# git status
On branch myfeature_monu
nothing to commit, working tree clean
root@ip-172-31-33-113:/tmp/starter-web# git brances
git: 'brances' is not a git command. See 'git --help'.

The most similar command is
        branch
root@ip-172-31-33-113:/tmp/starter-web# git show
commit 4beb7f097b54ab7cf08daf17972c3ab14432ae24 (HEAD -> myfeature_monu, origin/                                                      master, origin/HEAD, master)
Merge: 5c05047 e73f914
Author: Jason Taylor <jason@jasongtaylor.com>
Date:   Wed Sep 2 02:39:19 2015 -0400

    Merge pull request #6 from jasongtaylor/feature-readme

    Adding README file

root@ip-172-31-33-113:/tmp/starter-web# ls
404.html                          crossdomain.xml  fonts       js
README.md                         css              humans.txt  robots.txt
apple-touch-icon-precomposed.png  favicon.ico      index.html  simple.html
root@ip-172-31-33-113:/tmp/starter-web# vi humans.txt
root@ip-172-31-33-113:/tmp/starter-web# git status
On branch myfeature_monu
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   humans.txt

no changes added to commit (use "git add" and/or "git commit -a")
root@ip-172-31-33-113:/tmp/starter-web# git commit -am "my changes"
[myfeature_monu d6ba25f] my changes
 Committer: root <root@ip-172-31-33-113.us-east-2.compute.internal>
Your name and email address were configured automatically based
on your username and hostname. Please check that they are accurate.
You can suppress this message by setting them explicitly. Run the
following command and follow the instructions in your editor to edit
your configuration file:

    git config --global --edit

After doing this, you may fix the identity used for this commit with:

    git commit --amend --reset-author

 1 file changed, 1 insertion(+)
root@ip-172-31-33-113:/tmp/starter-web# git checkout master
Switched to branch 'master'
Your branch is up to date with 'origin/master'.
root@ip-172-31-33-113:/tmp/starter-web# ls
404.html                          crossdomain.xml  fonts       js
README.md                         css              humans.txt  robots.txt
apple-touch-icon-precomposed.png  favicon.ico      index.html  simple.html
root@ip-172-31-33-113:/tmp/starter-web# vi README.md
root@ip-172-31-33-113:/tmp/starter-web# git commit -am "Changes to master for re                                                      basing example"
[master e3d1109] Changes to master for rebasing example
 Committer: root <root@ip-172-31-33-113.us-east-2.compute.internal>
Your name and email address were configured automatically based
on your username and hostname. Please check that they are accurate.
You can suppress this message by setting them explicitly. Run the
following command and follow the instructions in your editor to edit
your configuration file:

    git config --global --edit

After doing this, you may fix the identity used for this commit with:

    git commit --amend --reset-author

 1 file changed, 2 insertions(+), 1 deletion(-)
root@ip-172-31-33-113:/tmp/starter-web# git log --oneline --decorate --all --gra                                                      ph
* e3d1109 (HEAD -> master) Changes to master for rebasing example
| * d6ba25f (myfeature_monu) my changes
|/
*   4beb7f0 (origin/master, origin/HEAD) Merge pull request #6 from jasongtaylor                                                      /feature-readme
|\
| * e73f914 Adding Purpose section to README
| * 34f563b Adding README file
|/
* 5c05047 Copying files from initializr project zip file and then creating simpl                                                      e.html as basis for super simple pages
root@ip-172-31-33-113:/tmp/starter-web# git checkout myfeature_monu
Switched to branch 'myfeature_monu'
root@ip-172-31-33-113:/tmp/starter-web# git rebase master
First, rewinding head to replay your work on top of it...
Applying: my changes
root@ip-172-31-33-113:/tmp/starter-web# git log --oneline --decorate --all --gra                                                      ph
* 27e0497 (HEAD -> myfeature_monu) my changes
* e3d1109 (master) Changes to master for rebasing example
*   4beb7f0 (origin/master, origin/HEAD) Merge pull request #6 from jasongtaylor                                                      /feature-readme
|\
| * e73f914 Adding Purpose section to README
| * 34f563b Adding README file
|/
* 5c05047 Copying files from initializr project zip file and then creating simpl                                                      e.html as basis for super simple pages
root@ip-172-31-33-113:/tmp/starter-web# git commit -am "commit after rebasing"
On branch myfeature_monu
nothing to commit, working tree clean
root@ip-172-31-33-113:/tmp/starter-web# git log --oneline --decorate --all --gra                                                      ph
* 27e0497 (HEAD -> myfeature_monu) my changes
* e3d1109 (master) Changes to master for rebasing example
*   4beb7f0 (origin/master, origin/HEAD) Merge pull request #6 from jasongtaylor                                                      /feature-readme
|\
| * e73f914 Adding Purpose section to README
| * 34f563b Adding README file
|/
* 5c05047 Copying files from initializr project zip file and then creating simpl                                                      e.html as basis for super simple pages
root@ip-172-31-33-113:/tmp/starter-web# git status
On branch myfeature_monu
nothing to commit, working tree clean
root@ip-172-31-33-113:/tmp/starter-web# git chceckout master
git: 'chceckout' is not a git command. See 'git --help'.

The most similar command is
        checkout
root@ip-172-31-33-113:/tmp/starter-web# git checkout master
Switched to branch 'master'
Your branch is ahead of 'origin/master' by 1 commit.
  (use "git push" to publish your local commits)
root@ip-172-31-33-113:/tmp/starter-web# git checkout master^C
root@ip-172-31-33-113:/tmp/starter-web# git show branch
fatal: ambiguous argument 'branch': unknown revision or path not in the working                                                       tree.
Use '--' to separate paths from revisions, like this:
'git <command> [<revision>...] -- [<file>...]'
root@ip-172-31-33-113:/tmp/starter-web# git show branches
fatal: ambiguous argument 'branches': unknown revision or path not in the workin                                                      g tree.
Use '--' to separate paths from revisions, like this:
'git <command> [<revision>...] -- [<file>...]'
root@ip-172-31-33-113:/tmp/starter-web# git checkout master^C
root@ip-172-31-33-113:/tmp/starter-web# git diff master myfeatture_monu
fatal: ambiguous argument 'myfeatture_monu': unknown revision or path not in the                                                       working tree.
Use '--' to separate paths from revisions, like this:
'git <command> [<revision>...] -- [<file>...]'
root@ip-172-31-33-113:/tmp/starter-web# git diff master myfeature_monu
diff --git a/humans.txt b/humans.txt
index 5b037cf..36ca2c9 100644
--- a/humans.txt
+++ b/humans.txt
@@ -13,3 +13,4 @@

     HTML5, CSS3
     jQuery, Modernizr
+my changes
root@ip-172-31-33-113:/tmp/starter-web# git merge myfeature_monu
Updating e3d1109..27e0497
Fast-forward
 humans.txt | 1 +
 1 file changed, 1 insertion(+)
root@ip-172-31-33-113:/tmp/starter-web# git diff master myfeature_monu
root@ip-172-31-33-113:/tmp/starter-web# git log --oneline --decorate --all --gra                                                      ph
* 27e0497 (HEAD -> master, myfeature_monu) my changes
* e3d1109 Changes to master for rebasing example
*   4beb7f0 (origin/master, origin/HEAD) Merge pull request #6 from jasongtaylor                                                      /feature-readme
|\
| * e73f914 Adding Purpose section to README
| * 34f563b Adding README file
|/
* 5c05047 Copying files from initializr project zip file and then creating simpl                                                      e.html as basis for super simple pages
root@ip-172-31-33-113:/tmp/starter-web# git branch -d myfeature_monu
Deleted branch myfeature_monu (was 27e0497).
root@ip-172-31-33-113:/tmp/starter-web# git branch -a
* master
  remotes/origin/HEAD -> origin/master
  remotes/origin/master
