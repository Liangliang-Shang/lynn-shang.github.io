Title: Python & SQLite
Date: 2016-02-25 20:50  
Category: Python  
Tags: Python, DB, SQL, SQLite
Slug: python_sqlite  
Author: lshang  
Summary: Python and SQLite  

```python
#!/usr/bin/env python
# -*- coding: utf-8 -*-

import sqlite3

# database    = "example.db"      # -> a file that resides on FS
# database    = ":memory:"        # -> a database that resides in RAM
database    = ":memory:"
connection  = sqlite3.connect(database)
cursor      = connection.cursor()

sql_crt_tab_users = '''CREATE TABLE users (
    id INTEGER PRIMARY KEY AUTOINCREMENT, 
    user char(10) NOT NULL, 
    age SMALLINT
)
'''

sql_add_user = '''INSERT INTO users VALUES (
    NULL, 
    ?, 
    ?
)
'''

sql_get_user = '''SELECT * FROM users'''
sql_del_user = '''DELETE FROM users'''

def getAllUsers():
    cursor.execute(sql_get_user)
    for row in cursor.fetchall():
        print(("%8d %10s %3s") % (row[0], row[1], row[2]))

def delAllUsers(id):
    if int(id): 
        sql = sql_del_user + ''' WHERE id = ''' + str(id)
        print sql
        cursor.execute(sql)

# a shortcut for cursor.execute(sql)
connection.execute(sql_crt_tab_users)

# add one user with placeholders 
userA = ('a', 30)
print("sqlite db [%s]: Adding user %s, age %d" % (database, userA[0],
userA[1]))
cursor.execute(sql_add_user, ('a', 30))
print(("sqlite db [%s]: %d row(s) impacted!") 
    % (database, cursor.rowcount))
print("sqlite db [%s]: All users" % database)
connection.commit()
getAllUsers()

# add three users one time
users = [('b', 27), ('c', '44'), ('d', 18)]
print("sqlite db [%s]: Adding users %s" % (database,users))
cursor.executemany(sql_add_user, users)
print(("sqlite db [%s]: %d row(s) impacted!") 
    % (database, cursor.rowcount))
print("sqlite db [%s]: All users" % database)
connection.commit()
getAllUsers()

userUnknown = ('unknown', 0)
print("sqlite db [%s]: Adding user %s, age %d" % 
    (database, userUnknown[0], userUnknown[1]))
cursor.execute(sql_add_user, userUnknown)
print(("sqlite db [%s]: %d row(s) impacted!") 
    % (database, cursor.rowcount))

print(("sqlite db [%s]: All users before commit") % database)
getAllUsers()

print(("sqlite db [%s]: Rolling back...") % database)
connection.rollback()
print(("sqlite db [%s]: All users after rolling back") % database)
print("sqlite db [%s]: All users" % database)
getAllUsers()

print("sqlite db [%s]: %d row(s) impacted!" 
        % (database, connection.total_changes))
cursor.close()
connection.close()
```
