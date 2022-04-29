# Level 4
## Hashing and Salting (using bcrypt)

### Requirements
```
   npm i bcrypt@3.0.2             // @version
```

## Usage

```
   const bcrypt = require("bcrypt");
   const saltRound = 10;             // recommend to use 10 salting rounds
   const mongoose = require("mongoose");
   monngoose.connect("mongodb://localhost:27017/UserDB", {useNewUrlParser:true});
   const userSchema = {
    email:string,
    password:string
   };

   const User = new mongoose.modal("User",userSchema);

   app.post("/register" , function(req,res){
    bcrypt.hash(req.body.password,saltRounds,function (err,hash){
      const newUser = new User({
        email:req.body.email;
        password:hash;
      });
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
     bcrypt.compare(password, foundUser.password,function (err,result){
      if(result===true)
        res.render("home")
     });
   }
  }
  });
  });
