# Level 2
## Database Encryption

### Using mongoose-encryption

#### To install the package:
```
    $ npm i mongoose-encryption
```

## Code Example

```
   const mongoose = require("mongoose");
   const encrypt = require("mongoose-encryption");
   monngoose.connect("mongodb://localhost:27017/UserDB", {useNewUrlParser:true});
   const userSchema = {
    email:string,
    password:string
   };

   const secret = "This is our little secret";        // The Key Store this in .env file
   userSchema.plugin(encrypt,{secret:secret,encryptedFields:["password"]});

   const User = new mongoose.modal("User",userSchema);

   app.post("/register" , function(req,res){
    const newUser = new User({
    email:req.body.email;
    password:req.body.password;
    });
     newUser.save(function (err){
     if(err)
       console.log(err);
       else{
       res.render("home");
       }
     }); 
   });

  app.post("/login",function(req,res){
  const username = req.body.username;
  const password = req.body.password;
  User.findOne({email:username},function(err,foundUser){
  if(err)
    console.log(err);
  else{
   if(foundUser){
    if(foundUser.password===password)
    {
      res.render("home");
    }
   }
  }
  });
  });
```

## Environment Variables

### Installation 
```
   $ npm i dotenv
```
### Usage
```
   require ('dotenv').config();
```
  
###### In root folder create .env file

``` 
   // In file .env
   SECRET = VALUE(value);
```
####### To access the variables in main js file

```
    console.log(process.env.value);
```
