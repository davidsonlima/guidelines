## Instalação

### 11gR2

```
$ ./runInstaller -ignoreSysPrereqs -silent -responseFile `pwd`/response/db_install.rsp

$ dbca -silent -createDatabase \
  -templateName General_Purpose.dbc \
  -gdbname RADIX -sid RADIX -responseFile NO_VALUE \
  -characterSet AL32UTF8 \ # or WE8MSWIN1252
  -sysPassword ******** \
  -systemPassword ******** \
  -databaseType MULTIPURPOSE \
  -automaticMemoryManagement false \
  -storageType FS
  
  
$ export ORACLE_SID=RADIX
  
$ sqlplus /nolog
```
  
#### Links

https://oracle-base.com/articles/vm/installation-of-an-oracle-database-on-azure
https://docs.oracle.com/cd/E11882_01/server.112/e25494/create.htm
