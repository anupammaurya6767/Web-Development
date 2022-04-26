# Express  <img alt="Express" src="https://img.shields.io/badge/-Express-success?style=flat-square&logo=express&logoColor=white"/>

# 1. Creating a server using Express :
&nbsp;  Move to the location where you want to create files and open that location in terminal (command line)
 ```mkdir my-express-server
    cd my-express-server
    touch server.js
    npm init 
 ```
 
 # 2. Installing Express in the project
 ```npm install express```
 
 # 3. Start editing server.js file
 
 ``` // jshint esversion:6
 
     const express = require("express");
     
     const app = express();
     
     app.listen(3000,function(){
     console.log("Server started on port 3000");
     });
 ```
 # 4. Handling Requests and Responses
 
  ``` // jshint esversion:6
  
     const express = require("express");
     
     const app = express();
     
     app.use(express.static(__dirname + 'location folder of css and javascript files')); // In oder to use the required css and javascript files of html
     
     // Handling Requests and Responses at "/" (Root Directory)
     
     app.get("/",function(req,res){
     res.send("<h1>Hello World!</h1>"); // for sending any text message
     res.sendFile(__dirname,'location of html file'); // for sending html file as a response
     });
     
     // Processing post requests
     
     app.post("/",function(req,res){
       // Your Code
     });
     
     app.listen(3000,function(){
     console.log("Server started on port 3000");
     });
 ```
 
# 5. Using Body-Parser
``` // It is used to access the site data eg. form data ```
  ## Installing Body-Parser
    ```npm install body-parser```
    
  ## In File server.js
    
  ``` // jshint esversion:6
  
     const express = require("express");
     
     const app = express();
     
     const bodyParser = require("body-parser");
     
     app.use(bodyParser.urlencoded({extended:true}));
     
     app.use(express.static(__dirname + 'location folder of css and javascript files'));
     
     app.get("/",function(req,res){
     res.send("<h1>Hello World!</h1>");
     res.sendFile(__dirname,'location of html file');
     });
     
     
     app.post("/",function(req,res){
        console.log(req.body); // gives you data also add " .name attribute value of input "
     });
     
     app.listen(3000,function(){
     console.log("Server started on port 3000");
     });
 ```

# 6. Integrating API to our Express app

    ```
    // jshint esversion:6
  
     const express = require("express");
     
     const app = express();
     
     const bodyParser = require("body-parser");
     
     const https = require("https"); // For https request
     
     app.use(bodyParser.urlencoded({extended:true}));
     
     app.use(express.static(__dirname + 'location folder of css and javascript files'));
     
     app.get("/",function(req,res){
     https.get("url",function(response){
     response.on('data',function(data){
     const dataFromAPI = JSON.parse(data); // To convert data into Json format
     console.log(dataFromAPI);
     
     // We use write when we have to send multiple times because we only use res.send() one time 
     
     res.write("");
     res.write("");
     res.send();
     })
     })
     });
     
     
     app.post("/",function(req,res){
        console.log(req.body);
     });
     
     app.listen(3000,function(){
     console.log("Server started on port 3000");
     });
 ```
      
    
