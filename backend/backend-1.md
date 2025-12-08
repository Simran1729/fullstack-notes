###### **global catches:**

if your server crashes, someone might read your logs, so there is this

GLOBAL CATCHES.

//another middleware that you put at the end

//you need to use it at then once in your code, and if there is ever

an error/exception in your route, the control reaches your global catch

so that your logs don't get exposed

app.use(err, req, res, next) => {

//any middleware you write with four args it is treated as a global catch

res.json({

msg : "Sorry seomthing is up with our server"

})

}

###### **authentication and zod:**

1. use json web token for authentication - json webtokens give three functions mainly:

- sign ({"data"}, passowrd_or_your_key) : your encoded token
- verify (token, password) : it verifies if the signature or the token is valid or not, like anyone can see it or decode it
- decode(token) : gives us the data or decodes the token
  so only the server with the password can verify if this token is valid or not

2. sql is better and prisma is the best ORM rigth now to use

3. fetch api is provided by the browswer, axios is a wrapper over it

4. Hashing is one way, only you can hash your password, can't get password from the hash

5. Encryption is two way, can go from ecryted data to password and vice versa
