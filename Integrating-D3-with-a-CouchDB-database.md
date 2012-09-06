Say, you want to save your D3 application in a CouchDB database. This is just a proof of concept that this is possible. I use the »Focus + Context« diagram by Mike Bostock (http://bl.ocks.org/1667367) as an example.

Prerequesites:
- A running CouchDB (see http://couchdb.apache.org/; in my Windows installation CouchDb is started as a Windows service when Windows starts).
- An installation of couchapp (how to install couchapp, see http://couchapp.org/page/index).
- Your favorite editor.

The steps are quite simple.
* In your favorite workspace create a new folder and name it say **d3apps**. 
* Within this folder create a file named **.couchappr**. This file will be used by couchapp to create the CouchDB database.
* Open this file in your text editor and add an empty object: **{}**. Nothing more is required for couchapp to create the database!
* In the **d3apps** folder create a subfolder named **_attachments**.
* Copy **d3.v2.min.js** into the subfolder **_attachments**.
* Copy **index.html** and **sp500.csv** of »Focus + Context« example into the subfolder **_attachments**.

Now you should have the following folder/file structure:

<code>
d3apps<br>
    _attachments<br>
        d3.v2.min.js<br>
        index.html<br>
        sp500.csv<br>
     .couchappr<br>
</code>

Open a command line window and navigate to your **d3apps** folder.
In the command line window issue the command (of course, couchapp must be on your path; otherwise you must supply the full path to couchapp.bat):

**couchapp push d3apps**

That's it. Now in your browser, you can navigate to http://127.0.0.1:5984/d3apps/_design/d3apps/index.html and admire your d3 application.

Of course, this just shows that you can integrate and serve (!) D3 applications from a CouchDB without any middleware. This example doesn't use any features of CouchDB to store and deliver the data. This will be topic of future examples.




