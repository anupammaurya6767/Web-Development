# Level 1 
## Register Users With Username And Password

```
   const mongoose = require("mongoose");
   monngoose.connect("mongodb://localhost:27017/UserDB", {useNewUrlParser:true});
   const userSchema = {
    email:string,
    password:string
   };

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
