# lib_mysqludf_sys
A UDF library with functions to interact with the operating system. These functions allow you to interact with the execution environment in which MySQL runs.

#  install 

## ubuntu

```sh
git clone git@github.com:ngocbd/lib_mysqludf_sys.git
cd lib_mysqludf_sys/
./install.sh
    
    
    
    
    
    
    
    
    
    
    
    
    
``
## centos

in centos install.sh script will  not work properly. 
```sh
git clone git@github.com:ngocbd/lib_mysqludf_sys.git

cd lib_mysqludf_sys/
gcc -Wall -m64 -I/usr/include/mysql -I. -shared lib_mysqludf_sys.c -o /usr/lib64/mysql/plugin/lib_mysqludf_sys.so -fPIC
service mysqld restart
mysql -uroot -p
```
exec sql script or paste to mysql console 
```sql
DROP FUNCTION IF EXISTS lib_mysqludf_sys_info;
DROP FUNCTION IF EXISTS sys_get;
DROP FUNCTION IF EXISTS sys_set;
DROP FUNCTION IF EXISTS sys_exec;
DROP FUNCTION IF EXISTS sys_eval;
CREATE FUNCTION lib_mysqludf_sys_info RETURNS string SONAME 'lib_mysqludf_sys.so';
CREATE FUNCTION sys_get RETURNS string SONAME 'lib_mysqludf_sys.so';
CREATE FUNCTION sys_set RETURNS int SONAME 'lib_mysqludf_sys.so';
CREATE FUNCTION sys_exec RETURNS int SONAME 'lib_mysqludf_sys.so';
CREATE FUNCTION sys_eval RETURNS string SONAME 'lib_mysqludf_sys.so'
```

