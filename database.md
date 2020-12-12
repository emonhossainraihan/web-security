## Atomicity 

All or none. if a failure happened during transaction, db failure, or one of the queries failed. 


## Isolation

Concurrency, is transaction isolated from other inflight transactions?  if a transaction is in flight does it see changes from other inflight transactions? Does is it see any changes? Does it only see committed changes. Does leading to inconsistent results.   
 
Problems arising from isolation (read phenomenons) 
- dirty reads
- Non repeatable reads
- Phantom reads 

![](https://i.imgur.com/fUjt4Vw.png)

![](https://i.imgur.com/r6E8lFw.png)

![](https://i.imgur.com/VKyizZf.png)


Isolation levels
- Read uncommitted
- Read committed 
- Repeatable read 
- Serializable 

![](https://i.imgur.com/I5Q3j60.png)

![](https://i.imgur.com/uJbvvj2.png)

## Durability

When I commit a transaction does my changes stay durable after the database restarts/crashes etc. 

## Consistency

Consistency from referential integrity keys 

Does the number of likes on a picture = the number of rows that the picture got on another table? If a delete a picture does all the likes of that pictures go away on the other table.

Consistency in reads 

If I committed something does everybody see it immediately or are they going to get an old value?

Consistency in concurrency

Is the view of a transaction in flight consistent? Are other inflight transactions making changes to the database affects that transaction view?
