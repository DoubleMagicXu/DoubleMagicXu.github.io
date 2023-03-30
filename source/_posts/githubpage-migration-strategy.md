---
title: githubpage migration strategy
date: 2023-03-30 09:51:37
tags:
---
# githubpage migration strategy
## generate ssh key
``` 
ssh-keygen -t rsa -C "XXX@XXX.com"
//keep pressing ENTER
cat ~/.ssh/id_rsa.pub
//copy code
```
## [add new ssh key](https://github.com/settings/ssh/)

## [hexo migration](https://www.zhihu.com/question/21193762/answer/79109280)
1. create two branches,maseter and hexo.set hexo as default bracnch where we place hexo configuration files.
![defaut branch.png](https://s2.loli.net/2023/03/30/QYFqRu4lref9nG5.png)
2. pull
   ```
    git clone ..
   ```
3. push hexo branch
   ```
   git add .
   git commmit -m "xxx"
   git push -u origin master
   ```
4. push master branch
   ```
   hexo g -d
   ```