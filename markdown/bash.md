Title: Best Practice of BASH  
Date: 2016-02-19 20:41  
Category: Linux  
Tags: BASH, Linux, UNIX  
Slug: bash  
Author: lshang  
Summary: Best Practice of BASH  

## PS1
A much nicer PS1 to dispaly date/time with YYYYmmdd HH:MM:SS and username@hostname:path
```Shell
PS1="\D{%Y%m%d %H:%M:%S} \u@$(hostname):\$(pwd) \n$ "
export PS1
```

## path
Display pathes in each line
```Shell
# echo ${PATH} | sed -e 's/:/\n/g'
# echo ${PATH} | tr ':' "\n"
alias path='echo -e ${PATH//:/\\n}'
```
## pid
Get ps snapshot of *keyword* and their PIDs
```Shell
function pid {
    TEMP=$(tempfile)
    ps -ef | grep $1 | grep -v grep | tee $TEMP \
        && awk -F'[ \t]*' 'BEGIN { RS="\n"; ORS=" "} { print $2 } \ 
                            END { printf "\n" }' $TEMP 
}
```
```Text
20160215 21:06:58 lshang@elemos:/home/lshang 
$ pid apache
root      1336     1  0 20:14 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  1350  1336  0 20:14 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  1351  1336  0 20:14 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  1352  1336  0 20:14 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  1354  1336  0 20:14 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  9044  1336  0 20:33 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 10287  1336  0 20:45 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 10288  1336  0 20:45 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 10289  1336  0 20:45 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 11361  1336  0 20:56 ?        00:00:00 /usr/sbin/apache2 -k start
www-data 12121  1336  0 21:04 ?        00:00:00 /usr/sbin/apache2 -k start
1336 1350 1351 1352 1354 9044 10287 10288 10289 11361 12121 
```

## trunc  
Clear the content of a file, but keep the file and its properties like
permission  
```Shell
alias trunc='cat /dev/null > '
```
```Text
20160219 20:19:37 lshang@elemos:/tmp 
$ cat fileXi87BI && ls -larht fileXi87BI 
root      1326     1  0 20:11 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  1342  1326  0 20:11 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  1344  1326  0 20:11 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  1345  1326  0 20:11 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  1346  1326  0 20:11 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  1347  1326  0 20:11 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  7260  1326  0 20:15 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  7265  1326  0 20:15 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  7266  1326  0 20:15 ?        00:00:00 /usr/sbin/apache2 -k start
-rw------- 1 lshang lshang 675 Feb 19 20:19 fileXi87BI
20160219 20:19:59 lshang@elemos:/tmp 
$ trunc fileXi87BI 
20160219 20:20:07 lshang@elemos:/tmp 
$ cat fileXi87BI && ls -larht fileXi87BI 
-rw------- 1 lshang lshang 0 Feb 19 20:20 fileXi87BI
```

## .env.bash
source ~/.env.bash at ~/.bashrc
```Shell
if [ -f ~/.env.bash.lshang ]; then
    . ~/.env.bash.lshang
fi
```

## /etc/motd
[ASCII Art](http://www.ascii-art.de/)
```Shell
cat <<EOT
 
                                  _oo0oo_
                                 088888880
                                 88" . "88
                                 (| -_- |)
                                  0\ = /0
                               ___/'---'\___
                             .' \\\\|     |// '.
                            / \\\\|||  :  |||// \\
                           /_ ||||| -:- |||||- \\
                          |   | \\\\\\  -  /// |   |
                          | \_|  ''\---/''  |_/ |
                          \  .-\__  '-'  __/-.  /
                        ___'. .'  /--.--\  '. .'___
                     ."" '<  '.___\_<|>_/___.' >'  "".
                    | | : '-  \'.;'\ _ /';.'/ - ' : | |
                    \  \ '_.   \_ __\ /__ _/   .-' /  /
                ====='-.____'.___ \_____/___.-'____.-'=====
                                  '=---='
 
              ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
                        佛祖保佑    iii    永不死机
 
EOT
```
