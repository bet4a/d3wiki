[Part 1](https://github.com/mbostock/d3/wiki/Integrating-d3-with-a-CouchDB-database-1), 
[Part 2](https://github.com/mbostock/d3/wiki/Integrating-d3-with-a-CouchDB-database-2), 
[Part 3](https://github.com/mbostock/d3/wiki/Integrating-d3-with-a-CouchDB-database-3)

Loading static data from a csv is fine, but really to use the power of CouchDB you'll want to be using views as the data source for your visualisation. This allows you to easily modify your dataset by adding/removing/editing documents.

## Changes to the couchapp
First copy the app from a previous step over into `d3apps4`: 

    cp -r d3apps1 d3apps4

Next you'll need to make a view. Execute `couchapp generate view d3apps4 pricetimeseries` to create the view boiler plate. Remove the reduce function as we're not going to use that in this example (e.g. `rm d3apps4/views/pricetimeseries/reduce.js`). The reduce function is actually ideal for this kind of thing, you could have daily records being aggregated into single monthly records, but for simplicities sake we'll skip it for now.

The map function (`d3apps4/views/pricetimeseries/map.js`) should look like:

    function(doc) {
      if (doc.date && doc.price){
        emit(doc.date, doc.price);
      }
    }

Next we need to change the javascript in `d3apps4/_attachments/index.html` to use the json from the view instead of the static csv. There are lots of ways to do this (`jquery.couch.js`, `sag.js` to name a couple) but d3 has json support baked in, so lets use that directly. Once online, the view is available at `_view/pricetimeseries` (in relation to `index.html`) so we can replace the `d3.csv()` function with:

    d3.json("_view/pricetimeseries", function(viewdata) {
      // We just want rows from the view in the visualisation
      data = viewdata["rows"];
      data.forEach(function(d) {
        // the key holds the date, in seconds
        d.date = new Date(d.key);
        d.price = +d.value;
      });

    // rest of the visalisation code

As you can see we've had to pick out the `rows` from the view and change the data parsing to take into account the different format of the view data (see below). You can see the full `index.html` in this [gist](https://gist.github.com/3690530).

Once you've made these changes push the couchapp up into the database with 

`couchapp push d3apps4`

## Data import
If you visit your app now your visualisation won't have any data in it. We need to import the csv into CouchDB documents so that the view can process them. The [gist](https://gist.github.com/3690530) contains a python script, `import_csv.py`, to do just this. You'll need the excellent [requests](http://python-requests.org) library installed to use it. Copy the `import_csv.py` into `d3apps4` and go into that directory. Run the script via `python import_csv.py`,  if everything works you should see `<Response [201]>`. 

The script reads and uploads the csv data with each row being an individual document. It converts the data ("Sep 2012") into milliseconds during the import. This is to make sorting the date simpler - we could do that in the view or the d3 code but it's simpler to do it at acquisition time.

Once the data is uploaded go visit the application at http://127.0.0.1:5984/d3apps4/_design/d3apps4/index.html. You should see the visualisation, rendering data from the view. 