# sql_fun
sql

### create table withdates between 19000101 and 21000101
```
create table dates as with recursive mydates(tdate) as (
	select cast ('19000101' as date) tdate
	union all
	select cast (tdate + interval '1 day' as date) tdate
	from mydates 
	where tdate <= '21000101'
)
select * from mydates;
```
