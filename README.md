Setup DegreeVU
=============

Here is a wiki for setting up DegreeVU


##Step 1: Setup Node js on your computer

http://nodejs.org/download/

##Step 2: Setup mongodb on your computer

http://docs.mongodb.org/manual/installation/

**MAKE SURE YOU KNOW WHERE MONGODB IS IN YOUR FILE SYSTEM.**  There is a step that has you make a target directory with mongodb, so make sure you can navigate there and see the mongodb binaries (under /bin).

##Step 3: Get the Degree VU respository

Clone the repository to your desired directory:

git clone https://github.com/mcooley/DegreeVU.git

##Step 4: Download the list of courses

The list of courses are attached to this respository, titled courses.json...


##Step 5: Setup the local database and collection

First, you must start up the mongo server and shell. Go to your terminal and type...

cd /your/mongo/target/directory/mongo/bin

You should now be in the bin directory that is inside your mongodb directory.

./mongod

This command starts the mongo localhost.  If some warnings come up, do not worry about them, just make sure the local server is up.  If the server is working, then you shouldn't be able to use your terminal since it is now running the shell.

Another way to check if the server is up is if you go to your browser and type in:

localhost:27017 into the url bar, you should get the message...

**It looks like you are trying to access MongoDB over HTTP on the native driver port.**

Now open a new terminal window and navigate back to your mongo binaries folder where you opened the server.  To start the shell, run the command...

./mongo

Ignore warnings that may come up.  You should see a little *>* character, where you can type in commands.  Type in the following commands...

use degreevu
db.createCollection('courses')


This will setup up your database and collection.

##Step 6: Import the list of courses into your mongodb directory

Now exit the mongoshell with *Ctrl+C* but **Let the mongo server keep running**

Now type the following into a terminal window:

./mongoimport --db degreevu --collection courses --file /path/to/file/courses.json 


This should load all the proper courses into the database.  


##Step 7: Setup DegreeVU 

Navigate **into** the DegreeVU repository that you downloaded from Step 3 and run the command

npm install
npm install mongodb


