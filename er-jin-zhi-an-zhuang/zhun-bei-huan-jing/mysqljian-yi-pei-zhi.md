# MySQL 5.7 建议配置，MySQL 5.8类似。

\[client\]

default-character-set=utf8mb4

port=3306

socket=/var/lib/mysql/mysql.sock

\[mysql\]

default-character-set=utf8mb4

\[mysqld\]

character-set-client-handshake=FALSE

character-set-server=utf8mb4

collation-server=utf8mb4\_unicode\_ci

init\_connect='SET NAMES utf8mb4'

user=root

datadir=/opt/mysql

socket=/var/lib/mysql/mysql.sock

port = 3306

\#skip-grant-tables

skip\_ssl

explicit\_defaults\_for\_timestamp=1

\#open\_files\_limit=65535

back\_log = 1024

host\_cache\_size=0

skip-external-locking

skip-name-resolve

lower\_case\_table\_names=1

max\_allowed\_packet = 512M

table\_open\_cache = 1000

table\_definition\_cache = 1024

table\_open\_cache\_instances = 64

sort\_buffer\_size = 4M

join\_buffer\_size = 4M

read\_buffer\_size = 128M

read\_rnd\_buffer\_size = 128M

thread\_cache\_size = 768

thread\_stack = 512K

query\_cache\_size = 0

query\_cache\_type = 0

tmp\_table\_size = 32M

max\_heap\_table\_size = 32M

interactive\_timeout=2147483

wait\_timeout=2147483

max\_connections=5000

max\_connect\_errors=100000

expire\_logs\_days=2

sql\_mode=STRICT\_TRANS\_TABLES,NO\_ZERO\_IN\_DATE,NO\_ZERO\_DATE,ERROR\_FOR\_DIVISION\_BY\_ZERO,NO\_AUTO\_CREATE\_USER,NO\_ENGINE\_SUBSTITUTION

innodb\_data\_home\_dir=/opt/mysql

innodb\_data\_file\_path=ibdata1:10M:autoextend

innodb\_log\_group\_home\_dir=/opt/mysql

innodb\_buffer\_pool\_size=3G

innodb\_log\_file\_size=512M

innodb\_log\_buffer\_size=8M

innodb\_log\_files\_in\_group=3

innodb\_flush\_log\_at\_trx\_commit=1

innodb\_flush\_method=O\_DIRECT

innodb\_file\_per\_table=1

innodb\_open\_files=1000

innodb\_lock\_wait\_timeout=120

innodb\_thread\_concurrency=0

\[mysqldump\]

quick

max\_allowed\_packet = 16M

\[myisamchk\]

key\_buffer\_size = 256M

sort\_buffer\_size = 256M

read\_buffer = 2M

write\_buffer = 2M

\[safe\_mysqld\]

err-log=/opt/mysql/mysqld.log

pid-file=/var/run/mysqld.pid

