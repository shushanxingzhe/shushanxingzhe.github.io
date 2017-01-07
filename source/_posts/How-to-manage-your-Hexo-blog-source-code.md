---
title: How to manage your Hexo blog source code
date: 2017-01-07 11:34:53
tags:
---

[Demo Repository](https://github.com/shushanxingzhe/shushanxingzhe.github.io/tree/sourcecode)

## How to add a new branch to save hexo source code ##

```
cd /path/to/you/hexo
git init
git checkout -b sourcecode
git remote add https://github.com/shushanxingzhe/shushanxingzhe.github.io.git
git add .
git commit -m 'save source code'
git push origin sourcecode:sourcecode
```


## Get source from Github and add new blog ##

### Clone source ###
```
git clone -b sourcecode https://github.com/shushanxingzhe/shushanxingzhe.github.io.git github.io
```

### Update dependency ###
```
cd github.io
npm update
```
### Create New Blog ###
```
hexo new "New Blog Title Here"
#write you blog in the source/_posts directory
hexo s
#run server on local,and check it
```

### Generate and Deploy ###
```
hexo d -g
```

### Update source code to Github ###
```
git add .
git commit -m 'add new blog'
git push
```



