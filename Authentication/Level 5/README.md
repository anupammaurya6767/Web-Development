# Level 5
## Cookies & Sessions (using passport)

### Requirements
```
   npm i passport passport-local passport-local-mongoose express-session
```

## Usage

```
   const session = require("express-session");
   const passport = require("passport");
   const passportLocalMongoose = require("passport-local-mongoose");
   const mongoose = require("mongoose");
   app.use(session({
    secret: " ",
    resave:false,
    saveUnlimited:false
   }));
   
   app.use(passport.initialize());
   app.use(passport.session());
   monngoose.connect("mongodb://localhost:27017/UserDB", {useNewUrlParser:true});
   mongoose.set("useCreateIndex",true);
   const userSchema = {
    email:string,
    password:string
   };
   
   userSchema.plugin(passportLocalMongoose);

   const User = new mongoose.modal("User",userSchema);
   passport.User(User.creatStrategy());
   passport.serializeUser(User, serializeUser());
   passport.deserializeUser(User,deserializeUser());

   app.post("/register" , function(req,res){
    User.register({username:req.body.username},req.body.password,function(err,user){
     if(err)
     {
       console.log(err);
     }else{
      passport.authenticate("local")(req,res,function(){
       res.redirect("home");
      });
     }
    });
    
  app.get("/home",function (req,res){
   if(req.isAuthenticated()){
     res.render("home");
   }else{
    res.redirect("/login");
   }
  });

  app.post("/login",function(req,res){
    const newUser = new User({
    email:req.body.email,
    password:req.body.password
    });
    req.login(user,function(err){
     if(err)
      console.log(err);
     else{
       passport.authenticate("local")(req,res,function(){
          res.redirect("home");
       })
     }
    });
   });
   
   app.get("/logout",function (req,res){
    req.logout();
    res.redirect("/");
   });
   
```
