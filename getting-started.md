---
layout: default
title: Impressory user documentation
---

## Hosting your course

<p class="lead">
Impressory is open source software.  That means you can freely run your own Impressory server to host as many courses as you like, or you can run your course on one that someone else has already set up &mdash; running your course in the cloud.
</p>
<p class="lead">
We have a server up and running for Design Computing Studio 2 at The University of Queensland at <a href="http://impressory.com">impressory.com</a>.  

If you'd like to run a course on our server (which is as simple as logging in and clicking "create course"), please get in touch.
</p>


<p class="lead">
Impressory can also be hosted on <a href="http://heroku.com">Heroku</a> for free.
</p>

### Hosting a course on Impressory.com

<p class="lead">
<a href="http://impressory.com">Impressory.com</a> is the server we're using for teaching Design Computing Studio 2 at The University of Queensland. If you would like to place your course on it, please send an email to ask first, as it's not yet a commercial service but still a work in progress.
</p>


### Running Impressory on your own server

To run Impressory on your own server:

1. Install [MongoDB](http://mongodb.org), the database that Impressory uses.
2. Install [Java](http://java.oracle.com). Impressory is written in Scala, which runs using the Java virtual machine.
3. Download the Impressory distribution zip file (not yet available)
4. Unzip the zip file
5. Run the `start` script.
6. Browse to http://localhost:9000 and sign up &mdash; the first user to register is given admin rights.

If you want to set up social integration, such as allowing students to log in with Twitter or GitHub accounts, you will need to register with GitHub, Twitter, etc to obtain an application client key and secret from them. You'll then need to set those keys and secrets in environment variables for Impressory to use.  Instructions for this will follow.

### Build and run Impressory from source <small>&mdash; the techie way</small>

Impressory is an open source project. This means that one way to run the server is to compile and run the source code.
These instructions assume you intend to run the server on Linux or Mac.  (We'll develop Windows instructions in due course.)

1. Install [MongoDB](http://mongodb.org), the database that Impressory uses.
2. Install [Java](http://java.oracle.com). Impressory is written in Scala, which runs using the Java virtual machine.
2. Install [sbt](http://www.scala-sbt.org), the Scala Build Tool.  (It's not very big.)
3. Clone the sourcecode repository from [GitHub](http://github.com/impressory/impressory)
4. Check Impressory works from sbt
      
       > sbt run

   This will compile and run the code from sbt -- by default it starts on port 9000, so if you browse to http://localhost:9000
   you should see your server.  However, running it this way, the server will exit when you close sbt.

5. Build the distribution zip file

       > sbt dist

   This builds a zip file containing everything you need to run the server (except installing the database).

6. Unzip and run the distribution zip file

       > unzip impressory-0.1.zip
       > cd impressory-0.1
       > chmod u+x start
       > nohup ./start > log.out 2> err.out &

   Unzipping the distribution zip, there is a start script that will run the server. First we make sure we have execute permissions on the start script (`chmod u+x`) and then we run it.  `nohup` ensures that when we close the terminal we
   ran it from, the server will keep on running, and will put any terminal output from the process into out.log and err.log
 
7. Log in to the server. The first user signed up to the server is given administrative rights.

If you want to set up social integration, such as allowing students to log in with Twitter or GitHub accounts, you will need to register with GitHub, Twitter, etc to obtain an application client key and secret from them. You'll then need to set those keys and secrets in environment variables for Impressory to use.  Instructions for this will follow.



### Running Impressory on Heroku

Heroku is a platform that lets you run services in the cloud.  Impressory runs successfully on their free tier, if you add a MongoDB database (small ones are available free, which should be enough for a few courses).

We'll add detailed instructions shortly, but essentially what you do is:

1. Install the Heroku Toolbelt
2. Create a Heroku application
3. Add a MongoDB database to your Heroku application.
4. Set some environment variables on the Heroku application.
3. `git clone` the Impressory source code
4. Add your Heroku application as a `git remote`
4. `git push` the source code to Heroku.  Heroku will then build and run Impressory automatically for you.





