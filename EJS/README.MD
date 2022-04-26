#   What is Ejs?
<img src="https://img.shields.io/badge/Ejs-EJS-darkred">
What is the "E" for? "Embedded?" Could be. How about "Effective," "Elegant," or just "Easy"? EJS is a simple templating language that lets you generate HTML markup with plain JavaScript. No religiousness about how to organize things. No reinvention of iteration and control-flow. It's just plain JavaScript.

# Installation 

```
$ npm install ejs

```

# Configuration

## Files To make

~ Create a folder name "views" (It's Important)
~ Create a file "index.ejs"
~ In index.ejs write your code(html)
   ex: 
       ```
         <h1>It's a <%= var %></h1>
         
       ```
  ### Note : Use "<%= variable %>" for variables in ejs file.
## In server.js (main file of node)
```
app.set('view engine','ejs');
var day = "";
app.get('/',function(req,res)
{
  res.render("index (ejs file name)", {var(variable name in ejs file) : day(value passes to that variable)});

});

```
## To run Javascript Code in ejs file

### Use "<% javascript code %>" for each line of code.

## For components 

### Make header.ejs or whatever components you want to make, add required code in it.
 #### To include that components in main index.ejs file
  ```
  <%-include("header")-%>
  
  ```
