elasticsearch-sql
=================

> use elasticsearch like sql , and use es function in sql .
>  
> it dev on elasticsearch 1.3.2 jdk 1.7
> 
> run on elasticsearch 1.x jdk7
>
> can run client or plugin on server
> 
> ###thanks by @温少 and @elasticsearch @Medcl 


# SETUP 

* plug

````

./bin/plugin -u http://maven.nlpcn.org/org/nlpcn/elasticsearch-sql/0.1/elasticsearch-sql-0.1.jar --install sql 

````

* search by search

````

http://localhost:9200/_sql?sql=select * from * limit 10

````

* explain sql to es script

````
http://localhost:9200/_sql/_explain?sql=select * from * limit 10

```` 


# Simple Case

==================

> ###you can use it by sql .

* Query

    	select * from blank where age >30 and gender ="m" ;

* Aggregation

        select count(*),sum(age),min(age) as m,max(age),avg(age) from bank group by gender order by sum(age),m desc

> ###beyond sql

* Search

        select address from bank where address= matchQuery('880 Holmes Lane') order by _score desc limit 3 
        

* expand Aggregation Range
	
	+ range age group 20-25,25-30,30-35,35-40

			select count(age) from bank  group by range(age, 20,25,30,35,40) 


	+ range date group by day 
	
			select online from online  group by date_histogram(field='insert_time','interval'='1d') 

	+ range date group by your config
	
			select online from online  group by date_range(field='insert_time','format'='yyyy-MM-dd' ,'2014-08-18','2014-08-17','now-8d','now-7d','now-6d','now')



# NOW

> 列出已经实现的功能
*  ES TopHits
*  ES MISS
*  SQL select
*  SQL COUNT distinct
*  SQL where
*  SQL AND & OR
*  SQL Order By
*  SQL 通配符
*  SQL In
*  SQL Between
*  SQL Aliases
*  SQL Not Null
*  SQL(ES) Date
*  SQL avg()
*  SQL count()
*  SQL last()
*  SQL max()
*  SQL min()
*  SQL sum()
*  SQL Nulls
*  SQL isnull()
*  SQL Group By
*  SQL now()

# FEATURE

*  SQL insert
*  SQL update
*  SQL delete
*  ES functions