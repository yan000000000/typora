

### upload a repo

```
git remote add origin https://github.com/yan000000000/laughing-broccoli.git
git branch -M main
git push -u origin main
```

`git remote add` used to add a new remote repository

`origin` common convention to name the remote repo origin

`-M main` used to rename the default branch from master to main

`-u` stands for set upstream.

#### upload all the branch

```
git push --all
```

### second and eternal

```c++
git remote set-url origin https://github.com/yan000000000/typora.git // only if you change a repo, change the current named origin remote address into the new repo
git remote add <name> <address> // add a new remote with other repo
git remote -v // really important! to check how many remote and its respective address
git branch -M main // used to rename the default branch from master to main
git push -u origin main // push the main branch through the origin remote to github

```



### update repo



```
git fetch (shows all the traffic and historical version)
git merge (to merge the repo)

or

git pull
```

