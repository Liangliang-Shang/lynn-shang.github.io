Title: Best Practice of Git/GitHub  
Date: 2016-02-19 20:51  
Category: Linux  
Tags: Git, GitHub, Linux  
Slug: git_github  
Author: lshang  
Summary: Best Practice of Git/GitHub  

## Config
+ **Local Git Config**  
```Shell  
$ git config --global user.name "Lynn-Shang"
$ git config --global user.email "imshang@126.com"
$ git config --list
user.name=Lynn-Shang
user.email=imshang@126.com
20160219 22:19:34 lshang@elemos:/home/lshang 
$ cat .gitconfig 
[user]
    name = Lynn-Shang
    email = imshang@126.com
```

+ **Generate ssh rsa key**
```Shell
20160219 22:47:36 lshang@elemos:/home/lshang 
$ ssh-keygen -t rsa -C "imshang@126.com"
20160220 10:40:02 lshang@elemos:/home/lshang 
$ ls -larth .ssh
total 20K
-rw-r--r--  1 lshang lshang  397 Feb 13 16:12 id_rsa.pub
-rw-------  1 lshang lshang 1.8K Feb 13 16:12 id_rsa
drwx------  2 lshang lshang 4.0K Feb 13 16:17 .
-rw-r--r--  1 lshang lshang 2.2K Feb 16 21:35 known_hosts
drwxr-xr-x 32 lshang lshang 4.0K Feb 20 10:39 ..
```
+ **Add ssh rsa pub key to GitHub**  
GitHub -> Settings -> SSH keys -> New SSH key ->  
Title: *title*  
Key: *text from id_rsa.pub*

## Enable automatically push
Command: git remote -v shows that we are using https
```Shell
$ git remote -v
master  https://github.com/Lynn-Shang/lynn-shang.github.io (fetch)
master  https://github.com/Lynn-Shang/lynn-shang.github.io (push)
origin  https://github.com/Lynn-Shang/lynn-shang.github.io (fetch)
origin  https://github.com/Lynn-Shang/lynn-shang.github.io (push)
```
Now switch to ssh
```Shell
$ git remote rm origin
$ git remote add origin git@github.com:lynn-shang/lynn-shang.github.io
$ git push
```

## Reference
[Git Reference](http://gitref.org/index.html)
