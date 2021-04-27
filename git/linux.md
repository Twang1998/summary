cat ~/.ssh/id_rsa.pub | ssh wangtao@ip tee -a .ssh/autorized_keys

ssh-copy-id -i /path/to/pubkey wangtao@ip 

没有-i也行

scp notes.md wangtao@ip:foobar.md

rsync -avP . wangtao@ip:cmd

rsync -avP . wangtao@ip:/tmp/cmd

tmux -a 



git add

git commit

git log --all --graph --decorate

git check out hash 回到任一snapshot maybe hash maybe master(reference)  dangoures opration

current change did not add and commit ,if you use check out , will cause error.   but can add -f

so it will destroy these no commit change

git diff  file.txt  

git diff hash file.txt   hash is one certion commit, give the diff between that commit and now.

no hash will compare with HEAD   equal to  git diff HEAD file.txt 

git diff hash HEAD hello.txt  give the difference between the snapshot hash and HEAD  in the file hello.txt...  



git check out hello.txt  let hello.txt back to HEAD ,and discard all the no add and commit change

insert mode how to move the cursor

git branch list all the branch

**git branch cat ** add a branch named cat

**git checkout cat ** HEAD focus on the cat, not the original master.

**git checkout -b cat** create a branch name cat



**git merge cat** before merge, confirm which commit you are.

** git branch --set-upstream-to=origin/master ** you can easy git push

**git fetch git merge**  **git pull**

**git clone --shallow** only contain the latest snapshot

blame + show

stash diff  stash pop = undo

bisect



