### Databases :

1. Why databases cant directly talk to the browser? Like why do we even need an http server exactly for?

2. Databases were created using protocols that broswers don't understand.

3. Databases don't have granual access as first class citizen. Very hard to do user sepcifics acces in them; i.e. databases don't have granular access if you have passwrod for the database, you have access to everything in it, and if you not , then nothing. So very 0 or 1.

4. So lets say even if you have an user on broswer who can talk directly to the db, then if they get access to db they can get access to entire db, so you won't be able make something like this, that if you have this password then you have access to this much data, and if that password, then that much data.

5. So that is why we need express or http servers in between , since that server has entire com plete access it need to do auth checks to give restricted access based on the user.

6. Even though there are some databases like firebase which can let you get rid fo http server and try best to give you granular access. So it kind of brought a paradigm shift.

7. Mongoose : A library used to interact with mongodb.

8. The thing is first you have to define the schema, but this might seem counterintuitive since mongodb is schemaless?

9. That is true, but mongoose makes you define schema for things like autocompletions/ validating data before it goes into the DB to make sure you're doing things right. Schemaless DBs can be very dangerous, using schemas in mongo makes it slightly less Dangerous

10. Clusters : A machine like AWS where you can run multiple databases.
