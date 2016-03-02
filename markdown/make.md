Title: Make & Makefile  
Date: 2016-03-02 21:20  
Category: Linux  
Tags: Linux, UNIX, Make, Makefile  
Slug: make  
Author: lshang  
Summary: Make & Makefile  

## Variable
```Makefile
CC=gcc
```

## Seperator
[Tab] is the seperator for commands: 

## .PHONY  
A phony target is one that is not really the name of a file; rather it is just
a name for a recipe to be executed when you make an explicit request. 
```Shell  
LOGDIR=.
.PHONY: clean
clean: 
	cd $(LOGDIR) && find . -type f -name "*.log" -exec rm {} \;
```

## Reference
Refer to [make](http://www.gnu.org/software/make/manual/make.html#Overview)
