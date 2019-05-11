# MySQL 5.7 建议配置，MySQL 5.8类似。

### 修改数据库存储位置

innodb\_data\_home\_dir=/opt/mysql 

innodb\_log\_group\_home\_dir=/opt/mysql

### **根据内存情况修改，建议大一些**

innodb\_buffer\_pool\_size=3G



```
[client]
default-character-set=utf8mb4
port=3306
socket=/var/lib/mysql/mysql.sock

[mysql]
default-character-set=utf8mb4

[mysqld]
character-set-client-handshake=FALSE
character-set-server=utf8mb4
collation-server=utf8mb4_unicode_ci
init_connect='SET NAMES utf8mb4'
user=root
datadir=/opt/mysql
socket=/var/lib/mysql/mysql.sock
port = 3306
#skip-grant-tables
skip_ssl
explicit_defaults_for_timestamp=1
#open_files_limit=65535
back_log = 1024
host_cache_size=0
skip-external-locking
skip-name-resolve
lower_case_table_names=1
max_allowed_packet = 512M
table_open_cache = 1000
table_definition_cache = 1024
table_open_cache_instances = 64
sort_buffer_size = 4M
join_buffer_size = 4M
read_buffer_size = 128M
read_rnd_buffer_size = 128M
thread_cache_size = 768
thread_stack = 512K
query_cache_size = 0
query_cache_type = 0
tmp_table_size = 32M
max_heap_table_size = 32M
interactive_timeout=2147483
wait_timeout=2147483
max_connections=5000
max_connect_errors=100000
expire_logs_days=2
sql_mode=STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION

innodb_data_home_dir=/opt/mysql
innodb_data_file_path=ibdata1:10M:autoextend
innodb_log_group_home_dir=/opt/mysql
innodb_buffer_pool_size=3G
innodb_log_file_size=512M
innodb_log_buffer_size=8M
innodb_log_files_in_group=3
innodb_flush_log_at_trx_commit=1
innodb_flush_method=O_DIRECT
innodb_file_per_table=1
innodb_open_files=1000
innodb_lock_wait_timeout=120
innodb_thread_concurrency=0

[mysqldump]
quick
max_allowed_packet = 16M

[myisamchk]
key_buffer_size = 256M
sort_buffer_size = 256M
read_buffer = 2M
write_buffer = 2M

[safe_mysqld]
err-log=/opt/mysql/mysqld.log
pid-file=/var/run/mysqld.pid
```



