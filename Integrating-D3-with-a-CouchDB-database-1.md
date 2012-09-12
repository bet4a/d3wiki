[Part 2](https://github.com/mbostock/d3/wiki/Integrating-d3-with-a-CouchDB-database-2), 
[Part 3](https://github.com/mbostock/d3/wiki/Integrating-d3-with-a-CouchDB-database-3), 
[Part 4](https://github.com/mbostock/d3/wiki/Integrating-d3-with-a-CouchDB-database-4)

## Proof of concept

Say, you want to save your D3 application in a CouchDB database. This is just a proof of concept that this is possible. I use the »Focus + Context« diagram by Mike Bostock (http://bl.ocks.org/1667367) as an example.

Prerequisites:
- A running CouchDB (see http://couchdb.apache.org/; in my Windows installation CouchDb is started as a Windows service when Windows starts).
- An installation of couchapp (how to install couchapp, see http://couchapp.org/page/index).
- Your favorite editor.

The steps are quite simple.
* In your favorite workspace create a new folder and name it say **d3apps1**. 
* Within this folder create a file named **.couchapprc**. This file will be used by couchapp to create the CouchDB database.
* Open this file in your text editor and add an empty object: **{}**. Nothing more is required for couchapp to create the database!
* In the **d3apps1** folder create a subfolder named **_attachments**.
* Copy **index.html** and **sp500.csv** of the »Focus + Context« example into the subfolder **_attachments**.

Now you should have the following folder/file structure:

```
d3apps1
    _attachments
        index.html
        sp500.csv
    .couchappr
```

Open a command line window and navigate to your **d3apps1** folder.
In the command line window issue the command (of course, couchapp must be on your path; otherwise you must supply the full path to couchapp.bat):

```
couchapp push d3apps1
```

That's it. Now in your browser, you can navigate to http://127.0.0.1:5984/d3apps1/_design/d3apps1/index.html and admire your d3 application.

Of course, this just shows that you can integrate and serve (!) D3 applications from a CouchDB without any middleware. There is still one external dependency: the d3 library, that is loaded from GitHub. This example doesn't use any features of CouchDB to store and deliver the data. This is just preliminary work for putting the data of my own applications into a CouchDB database. I thought this might be useful for others. How the d3 library and the data can be integrated into CouchDB is shown in [Integrating D3 with a CouchDB database 2](https://github.com/mbostock/d3/wiki/Integrating-D3-with-a-CouchDB-database-2).

