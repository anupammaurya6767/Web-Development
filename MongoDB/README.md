# MongoDB <img alt="MongoDB" src="https://img.shields.io/badge/-MongoDB-13aa52?style=flat-square&logo=mongodb&logoColor=white"/>
MongoDB is a source-available cross-platform document-oriented database program. Classified as a NoSQL database program, MongoDB uses JSON-like documents with optional schemas. 

## Steps to Install MongoDB on Ubuntu

### Step 1: Importing MongoDB Repositories
```
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 7F0CEB10
   
   echo "deb http://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.4 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.4.list
   
   sudo apt-get update
```
### Step 2: Installing MongoDB Packages
```
   sudo apt-get install -y mongodb-org
   
   sudo apt-get install -y mongodb-org=3.4 mongodb-org-server=3.4 mongodb-org-shell=3.4 mongodb-org-mongos=3.4 mongodb-org-tools=3.4
```

### Step 3: Launching MongoDB as a Service on Ubuntu

```
   sudo vim /etc/systemd/system/mongodb.service
   
```
##### Now, copy the following information in your configuration file:

```
   #Unit contains the dependencies to be satisfied before the service is started.
   [Unit]
   Description=MongoDB Database
   After=network.target
   Documentation=https://docs.mongodb.org/manual
  # Service tells systemd, how the service should be started.
  # Key `User` specifies that the server will run under the mongodb user and
  # `ExecStart` defines the startup command for MongoDB server.
  [Service]
  User=mongodb
  Group=mongodb
  ExecStart=/usr/bin/mongod --quiet --config /etc/mongod.conf
  # Install tells systemd when the service should be automatically started.
  # `multi-user.target` means the server will be automatically started during boot.
  [Install]
  WantedBy=multi-user.target
  
```

##### Once you’ve created your configuration file, you now need to update the system service using the following command:

```
   systemctl daemon-reload
```
##### Now, start/enable the updated systemd service for your MongoDB instance:
 ```  
   sudo systemctl start mongodb
 ```
##### With your MongoDB instance now up, you now need to verify if MongoDB started on port 27017. To do this, you can use the “netstat” command as follows:
 ```
   netstat -plntu
 ```
 
##### To verify if your MongoDB instance started correctly, you can use the status command as follows:
```
   sudo systemctl status mongodb
```

##### You can now enable the auto-start functionality for your system as follows:
```
   sudo systemctl enable mongodb
```



## To start mongo server locally
```
   mongod
```

## To enter in mongo shell 

```
   mongo
```

## CRUD

```
   use <database name>                           // to create  a database ex. products
   
   db                                            // to show currently working database
   
   db.products.insertOne(           
   {
     _id : 1, name:"Pen", price:1.20             // to insert new collection
   })
   
   show collections                              // to show cololections in current db
   
   ex : db.products.insertOne ({_id:2, name:"pencil", price:0.80})
   
   db.products.find()                            // to search for a data
   
   db.products.find({                             
     name:"pencil"                               // to search for a particular data
   
   })
   
   
   db.products.find({
     price: {$gt:1}                              //gt stands for greater than , searching on a condition
   
   })
   
   db.products.find({
     {_d:1},                                      
     {name:1}                                    // name is the projection (the thing which we want in return), 1 means which we want add 1 or else 0
   })
   
   db.products.updateOne({                       // to update any one value
   
   {_id:1},                                      // which you want to update
   {$set:{stock:32}}
   
   })
   
   db.products.deleteOne({                       // to delete a data
   
    {_id:2}                                      // filter (which want to delete
    
   })
   
 ```
 
 ## Relationships in mongoDB
 
 ```
    db.products.insert({
    _id:3,
    name:"Rubber",
    price:1.30,
    stock:43,
    reviews:[{
    
    authorName: "Sally",
    rating: 5,
    review: "Best product ever"
    
     }]
     })
