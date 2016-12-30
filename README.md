---
How to use
---

###Clone source
```
git clone -b sourcecode https://github.com/shushanxingzhe/shushanxingzhe.github.io.git github.io
```

###Update dependency
```
cd github.io
npm update
```
###Create New Blog
```
hexo new "New Blog Title Here"
#write you blog in the source/_posts directory
hexo s
#run server on local,and check it
```

###Generate and Deploy
```
hexo d -g
```

###Update source code to Github
```
git add .
git commit -m 'add new blog'
git push
```
