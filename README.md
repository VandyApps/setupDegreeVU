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

```git clone https://github.com/mcooley/DegreeVU.git```

##Step 4: Download the list of courses

The list of courses are attached to this respository, titled courses.json...


##Step 5: Setup the local database and collection

First, you must start up the mongo server and shell. Go to your terminal and type...

``` cd /your/mongo/target/directory/mongo/bin ```

You should now be in the bin directory that is inside your mongodb directory.

*./mongo*

This command starts the mongo localhost.  If some warnings come up, do not worry about them, just make sure the local server is up.  If the server is working, then you shouldn't be able to use your terminal since it is now running the shell.

Another way to check if the server is up is if you go to your browser and type in:

localhost:27017 into the url bar, you should get the message...

**It looks like you are trying to access MongoDB over HTTP on the native driver port.**

Now open a new terminal window and navigate back to your mongo binaries folder where you opened the server.  To start the shell, run the command

*./mongo*

Ignore warnings that may come up.  You should see a little *>* character, where you can type in commands.  Type in the following commands

```use degreeVU
db.createCollection('courses')```


This will setup up your database and collection.

##Step 6: Import the list of courses into your mongodb directory

Now exit the mongoshell with *Ctrl+C* but **Let the mongo server keep running**

Now type the following into a terminal window:

*./mongoimport --db degreeVU --collection courses --file /path/to/file/courses.json*


This should load all the proper courses into the database.  


##Step 7: Setup DegreeVU 

Navigate **into** the DegreeVU repository that you downloaded from Step 3 and run the command

npm install
npm install mongodb

##Step 8: Launch the App

*Make sure that the mongodb server is still running.*  Now while inside your DegreeVU repository, type:

*node app*

into the terminal.  This should start up the app with the message

*Express server listening on port 3000*

Launch the app in your browser by typing in:

*localhost:3000*

Check out the latest mockup of the web app using the url

*localhost:3000/planner*


Look at how the course api works with these commands:

*localhost:3000/courses/lookup?q=cs101*

-- Gets cs 101

*localhost:3000/courses/lookup?q=cs200%2b*

-- Gets all cs courses of 200 and above (%2b is the uri encoded + sign)

*localhost:3000/courses/lookup?q=cs200%2b,!cs300%2b*

-- Get all cs courses between 200 and 300

*localhost:3000/courses/lookup?q=bsci200%2b,!mns~*

-- Get all biology courses above 200 that do not count as material and natural sciences



