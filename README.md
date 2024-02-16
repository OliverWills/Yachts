# Yachts
Yacht Price Predication Model

# how to add new ads to 

# intall mongodb
# From a terminal, install gnupg and curl if they are not already available:
$ sudo apt-get install gnupg curl
# import the MongoDB public GPG key
$ curl -fsSL https://pgp.mongodb.com/server-7.0.asc | \
   sudo gpg -o /usr/share/keyrings/mongodb-server-7.0.gpg \
   --dearmor
# Create the list file /etc/apt/sources.list.d/mongodb-org-7.0.list for your version of Ubuntu
$ echo "deb [ arch=amd64,arm64 signed-by=/usr/share/keyrings/mongodb-server-7.0.gpg ] https://repo.mongodb.org/apt/ubuntu jammy/mongodb-org/7.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-7.0.list
# To determine which Ubuntu release your host is running, run the following command on the host's terminal:
$ cat /etc/lsb-release
# Reload local package database
$ sudo apt-get update
# To install the latest stable version, issue the following
$ sudo apt-get install -y mongodb-org
# Start MongoDB
$ sudo systemctl start mongod
$ sudo systemctl daemon-reload
# Verify that MongoDB has started successfully
$ sudo systemctl status mongod
# Begin using MongoDB
$ mongosh

# create databse in mongo shell
$ use db_name
#show database in list
$ db
#add collection
$ db_name.collection_name
#insert document
$ db.myNewCollection1.insertOne( { name:"geeksforgeeks" } )
#insert multiple documents
$ db.myNewCollection2.insertMany([{name:"gfg", country:"India"},
                                {name:"rahul", age:20}])

# intall pymongo
$ python3 -m pip install pymongo

# setup pymongo in python
import pymongo
from pymongo import MongoClient
client = MongoClient()
client = MongoClient("localhost", 27017)
client = MongoClient("mongodb://localhost:27017/")
db = client.test_database #Getting a Database
db = client["test-database"] #or (using dictionary style access):
collection = db.test_collection #Getting a Collection
collection = db["test-collection"] #or (using dictionary style access):

# how to insert data into a collection
post = {
    "author": "Mike",
    "text": "My first blog post!",
    "tags": ["mongodb", "python", "pymongo"],
    "date": datetime.datetime.now(tz=datetime.timezone.utc),
}
posts = db.posts
post_id = posts.insert_one(post).inserted_id
post_id
# bulk insert
new_posts = [
    {
        "author": "Mike",
        "text": "Another post!",
        "tags": ["bulk", "insert"],
        "date": datetime.datetime(2009, 11, 12, 11, 14),
    },
    {
        "author": "Eliot",
        "title": "MongoDB is fun",
        "text": "and pretty easy too!",
        "date": datetime.datetime(2009, 11, 10, 10, 45),
    },
]
result = posts.insert_many(new_posts)
result.inserted_ids

#how to query data with specific fields
cursor = db.inventory.find({"status": "A"}, {"item": 1, "status": 1})
#The operation corresponds to the following SQL statement:
SELECT _id, item, status from inventory WHERE status = "A"

# GIT - How it works
> $ Working Directory
> $ Staging Area
> $ Local Repo (HEAD)
> $ Remote Repo (MASTER)

Git Add = Working Directory -> Staging Area
Git Commit = Staging Area -> Local Repo
Git Push = Local Repo -> Remote Repo
Git Fetch = Remote Repo -> Local Repo
Git Merge = Local Repo -> Working Directory
Git Pull = Remote Repo -> Working Directory

# Uncommit Changes you just made to your Git Repo:
$ git reset HEAD~1 # HEAD is the Local Repo
# Remove the most recent commit
# Commit again!
$ git status # Lists all new or modified files to be committed

$ git remote -v # List the remote connections you have to other repositories.

$ git diff # To show the files changes not yet staged

$ git log

Each time you make changes that you want to be reflected on GitHub, the following are the most common flow of commands:

$ git add .
$ git status # Lists all new or modified files to be committed
$ git commit -m "Second commit"
$ git push -u origin master
