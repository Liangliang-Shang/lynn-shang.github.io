Title: Python & SQLite
Date: 2016-02-25 20:50  
Category: Python  
Tags: Python, DB, SQL, SQLite
Slug: python_sqlite  
Author: lshang  
Summary: Python and SQLite  

```python
#!/usr/bin/env python
import sqlite3

conn = sqlite3.connect("example.db")
curs = conn.cursor()
curs.execute("DROP TABLE ids")

curs.execute("CREATE TABLE ids (id INTEGER PRIMARY KEY AUTOINCREMENT)")
curs.execute("INSERT INTO ids VALUES (NULL)")
curs.execute("INSERT INTO ids VALUES (NULL)")
curs.execute("INSERT INTO ids VALUES (NULL)")
curs.execute("INSERT INTO ids VALUES (NULL)")

for row in curs.execute("SELECT * FROM ids"):
    print row
```
```Shell
$ python sqlite.py 
(1,)
(2,)
(3,)
(4,)
```
