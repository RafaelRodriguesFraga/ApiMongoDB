## <p align="center">A simple Books API developed in ASP.NET Core with MongoDB NoSQL based on Microsoft Tutorial</p> 

<p align="center">
    <img src="https://img.shields.io/badge/netcoreapp-3.0-purple">
    <img src="https://img.shields.io/badge/MongoDB-4.2-green">
</p> 

### Table of Contents

| No. | Content |
| --- | --------- |
|1| [Installing MongoDB](#installing-mongodb) |
|2| [Adding MongoDB to Environment Variables](#adding-mongoDB-to-environment-variables ) |
|3| [Starting MongoDB](#starting-mongodb) |
|4| [Creating Database and Collection](#creating-database-and-collection) |
|5| [Populating Database with Dummy Data](#populating-database-with-dummy-data) |
|6| [Listing all Books](#listing-all-books) |
|7| [Configuring your appsettings.json](#configuring-your-appsettingsjson) |

1. ### Installing MongoDB

     If you don't have installed yet MongdoDB on your computer, you can go to 
    [MongoDB Community Server Download Page](https://www.mongodb.com/try/download/community) and download it. 
    The install process is pretty straight-forward so you should not have any problems.  

**[⬆ Back to Top](#table-of-contents)**

2. ### Adding MongoDB to Environment Variables
    
    To use MongoShell you have to add MongoDB to the Windows Environment Variables. To do this, follow the steps below:   
 
    * Right-click the Computer icon and choose Properties, or in Windows Control Panel, choose System.  
    * Choose Advanced system settings. 
    * On the Advanced tab, click **Environment Variables**. 
    * Click on Path Variable. 
    * On the next screen click **New**.
    * Locate the directory where you installed and put the path there. Example: _C:\Program Files\MongoDB\Server\4.2\bin_ 
    
    _To make sure it's working, just open the cmd and type mongo --version. If it's working, you should see your MongoDB Shell 
    Version_

**[⬆ Back to Top](#table-of-contents)**
   
3. ### Starting MongoDB  
    
    Before we connect to Mongo, create a new folder somewhere in your computer to  store the data that will be generated. I created in *F:\MongoDB\BooksData* .The location doesn't matter. Just create it in a place that is easy to find.

    With that done and the cmd open, type: (without < >)

    **```mongod --dbpath <your_directory_path>```**

    In my case was:

    **```mongod --dbpath F:\MongoDB\BooksData```**

    Leave it running, open another cmd and type:

    **```mongo```**

    This will connect with your database

**[⬆ Back to Top](#table-of-contents)**

4. ### Creating Database and Collection

    Inside Mongo Shell, type:

    **```use BookstoreDb```**

    If doesn't exists, he'll create this database for us.

    Now, let's create our Books Collection. To do this, type:

    **```db.createCollection('Books')```**

    If created sucessfully, this message will appear:

   **```{ "ok" : 1 }```**

**[⬆ Back to Top](#table-of-contents)**

5. ### Populating Database with Dummy Data

    Let's add some dummy data to our database. To do this, execute:

    <pre>db.Books.insertMany([{'Name':'star Wars','Price':60,'Category':'Sci-Fi','Author':'George Lucas'}, {'Name':'Harry Potter And the Deathly Hallows','Price':50.10,'Category':'Fantasy','Author':'J.K Rowling'}])</pre>
    
    If added sucessfully, this message will appear:
    ```json
    {
        "acknowledged" : true,
        "insertedIds" : [
            ObjectId("5bfd996f7b8e48dc15ff215d"),
            ObjectId("5bfd996f7b8e48dc15ff215e")
        ]
    }
    ```
    
 **[⬆ Back to Top](#table-of-contents)**   
 
6. ### Listing all Books

    To make sure that our database is populated, type: 

    **```db.Books.find({}).pretty()```**

    And the result shall be our two books stored in the database
    ```json
    {
      "_id" : ObjectId("5bfd996f7b8e48dc15ff215d"),
      "Name" : "Star Wars",
      "Price" : 60,
      "Category" : "Sci-Fi",
      "Author" : "George Lucas"
    }

    {
      "_id" : ObjectId("5bfd996f7b8e48dc15ff215e"),
      "Name" : "Harry Potter And the Deathly Hallows",
      "Price" : 50.10,
      "Category" : "Fantasy",
      "Author" : "J.K Rowling"
    }
    ```

 **[⬆ Back to Top](#table-of-contents)** 

 7. ### Configuring your appsettings.json 

    Create a appsettings.json file and add this: 
  ```json
    {
      "BookstoreDatabaseSettings": {
      "BooksCollectionName": "Books",
      "ConnectionString": "mongodb://localhost:27017",
      "DatabaseName": "BookstoreDb"
  },
  ```

  **[⬆ Back to Top](#table-of-contents)**

  Now you'll be ready to use the API. Enjoy! :smile:

