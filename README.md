# Get-DatabaseObjects

Stop me if this sounds familiar: you have a reporting replica of your main production database. Maybe you're restoring the database there every day and it runs a day behind, or maybe you're a sadist and you use some form of replication to keep it up to date. Whatever the case, what happens? Sooner or later, objects (like views, stored procedures, etc) get created in there. And, since it's a reporting replica, you might not back it up often, at all. After all, it's just a copy of the data, right? We can just push it back down.

But, that's not always (if ever) realistic. Instead, wouldn't it be great if you could back up all the database objects in a database at the DDL level so that, if diseaster struck in the form of a bad deployment of code, or the reporting replica is corrupted, you could just restore production (or snapshot your replicas) and then reapply your object code? Well, you can! With PowerShell, even!

This script will take each object in your database, as well as users and permissions, and create a complete .sql file that you can re-run to put everything back as it was. Or, if you wanted to be really fancy, you could set the script to run and capture the object DDL and store the results in a database on a schedule, so you could have some sort of version control in case you ever need to roll back.

Please note the following:

1. This script requires the SQLPS module, which you can get by installing SQL Server Management Tools,
2. The code was created in Visual Studio, so if you don't want the entire solution, just dig into the folders,
3. If you want to store the output in a database, there's a SQL script that you can use to create the target table,
4. Never run something in production without testing it first.

Did you find this script useful? Me too! You should drop me a line at @pittfurg on twitter.
