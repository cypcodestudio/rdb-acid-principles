# RDB ACID Principles
Relational DB Acid Principles in Transactions

ACID properties are a set of principles that ensure reliable processing in database systems, particularly in relational databases. These properties guarantee that database transactions are processed reliably, even in cases of errors, power failures, or other issues. ACID stands for:

# Atomicity:

A transaction is treated as a single logical unit of work. Either all the operations within the transaction are completed successfully, or none are. If any part of the transaction fails, the entire transaction fails, and the database is left unchanged. This ensures that no partial updates are made.
begin transaction;

select * from wentity_account wa where wa.id =2;

update wentity_account wa set balance = 5000 where id =2;

select * from wentity_account wa where wa.id =2;

commit transaction;

select * from wentity_account wa where wa.id =2;

end transaction;



# Consistency:

A transaction must take the database from one valid state to another. This means that any data written to the database must comply with all predefined rules, such as constraints, triggers, or any combination of conditions that maintain data integrity.
begin transaction;

select * from wentity_account wa where wa.entity_id = 1;

insert INTO wentity_account values(default,33000,10000,1,1);

select * from wentity_account wa where wa.entity_id = 1;

commit;

select * from wentity_account wa where wa.entity_id  = 1;

end transaction;

# Isolation:

Transactions are executed in isolation from one another. Even if multiple transactions occur simultaneously, each transaction must behave as if it is the only one happening. This prevents transactions from interfering with each other, ensuring data integrity.
begin transaction;

select * from wentity_account wa where wa.entity_id = 1;

--update wentity_account wa set balance = 5000 where id =2;

insert INTO wentity_account values(default,45000,100000,1,1);

commit;

select * from wentity_account wa where wa.entity_id  = 1;

end transaction;

# Durability:

Once a transaction has been committed, the results are permanent. Even if the system crashes immediately afterward, the changes made by the transaction will persist, thanks to measures like logging or backups.
begin transaction;

select * from wentity_account wa where wa.entity_id = 1;

insert INTO wentity_account values(default,45000,100000,1,1);

commit;

select * from wentity_account wa where wa.entity_id  = 1;

end transaction;
