---
title: Efficient Command
---

``` bash
find . -type d -name ".svn"|xargs rm -rf            删除当前目录及子目录下的svn文件
svn st | awk '{if ($1 == "?") {print $2} }' | xargs svn add        svn添加所有新增文件
find . -type d -exec chmod 700 {} \;                   修改所有目录访问权限
find . -type f -exec chmod 600 {} \;                    修改所有文件访问权限
find . -name "*.php" -exec php  {} \;                    执行所有的php文件
grep -rli "helper('itags')" * | xargs -i@ sed -i "s/helper('itags')/helper('core')/g" @                将所有文件中包含的某字符串替换成另一字符串
grep -rli  --include=*.php.dec  '?><?php' . | xargs -i@ sed -i "s/?><?php/<?php/g" @ 

pcregrep -MHrin --color "addOrder.*\n.*1442470135100001" .      多行搜索（跨行）
set quote="'" ; phpgrep -i '\(select\|update\|delete\|insert\).*;\("\|${quote}\)'  . 搜索以分号;结尾的SQL语句
set quote="'" ; phpgrep -i '\(select\|update\|delete\|insert\).*[^;]\("\|${quote}\)'  . 搜索不以分号;结尾的SQL语句

find . -name '*.php.dec' -exec sh -c 'mv $0 ${0/.php.dec/.php};'  {} \;                搜索文件并重命名
find . -name 'article*' | sed -e "p;s/article/blog/" | xargs -n2 mv                       搜索文件并重命名(通用性强)

find . -name '*respond*' -exec sh -c ' grep -Hrin --color --exclude-dir=.svn "1442299522100003" $0'  {} \;     搜索文件 并查找文件中的的字符串
ps --no-headers -o "rss,cmd" -C php-fpm | awk '{ sum+=1 } END { printf ("%d\n", sum) }'         显示某程序进程总数

ps --no-headers -o "rss,cmd" -C php-fpm | awk '{ sum+=$1 } END { printf ("%d%s\n", sum/NR/1024,"M") }'    显示某程序平均内存占用数


ps --no-headers -o "rss,cmd" -C php-fpm | awk '{ sum+=$1 } END { printf ("%d%s\n", sum/1024,"M") }'
     显示某程序占用内存总数

ps --no-headers -o "rss,pcpu,cutime,cstime,utime,cmd" -C redis-server  | awk '{ sum+=$1;pcpu+=$2;cutime+=$3;cstime+=$4;utime+=$5 } END { printf ("rss:%d%s\n pcpu:%d\n cutime:%d\n cstime:%d\n  utime:%d\n", sum/1024,"M",pcpu,cutime,cstime,utime) }'                显示某程序占用的资源

```


