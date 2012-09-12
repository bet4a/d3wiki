[Part 1](https://github.com/mbostock/d3/wiki/Integrating-d3-with-a-CouchDB-database-1), 
[Part 2](https://github.com/mbostock/d3/wiki/Integrating-d3-with-a-CouchDB-database-2), 
[Part 4](https://github.com/mbostock/d3/wiki/Integrating-d3-with-a-CouchDB-database-4)
## Accessing data in a CouchDB database from a D3 application

First, make a copy of your complete **d3apps2** folder and store it in your workspace using the name **d3apps3**. Your folder structure should look as follows:

```
d3apps3
    _attachments
        d3.v2.min.js
        import.html
        index.html
        sp500.csv
    .couchappr<br>
```

To access the data in your **d3apps3** CouchDB, you need to change your **index.html** file. At the beginning you must insert two **jquery** scripts:

```
<!DOCTYPE html>
<meta charset="utf-8">

<script src="/_utils/script/jquery.js"></script>
<script src="/_utils/script/jquery.couch.js"></script>

<script src="d3.v2.min.js"></script>

<style>
```

The **d3.csv** function is no longer needed. Instead you retrieve the data from the database. Replace the function

```
    d3.csv("sp500.csv", function(data) {
        ...
    });

```

completely by following code:

```
    // This function replaces the d3.csv function.
    $.couch.db("d3apps3").openDoc("sp500", {
        success : function (doc) {

            var data = doc.data;

            data.forEach(function(d) {
                d.date = formatDate.parse(d.date);
                d.price = +d.price;
            });

            x.domain(d3.extent(data.map(function(d) { return d.date; })));
            y.domain([0, d3.max(data.map(function(d) { return d.price; }))]);
            x2.domain(x.domain());
            y2.domain(y.domain());

            focus.append("path")
                .data([data])
                .attr("clip-path", "url(#clip)")
                .attr("d", area);

            focus.append("g")
                .attr("class", "x axis")
                .attr("transform", "translate(0," + height + ")")
                .call(xAxis);

            focus.append("g")
                .attr("class", "y axis")
                .call(yAxis);

            context.append("path")
                .data([data])
                .attr("d", area2);

            context.append("g")
                .attr("class", "x axis")
                .attr("transform", "translate(0," + height2 + ")")
                .call(xAxis2);

            context.append("g")
                .attr("class", "x brush")
                .call(brush)
                .selectAll("rect")
                .attr("y", -6)
                .attr("height", height2 + 7);
        },
        error : function (status) {
            console.log("Doc not found");
            console.log("*** error:", status);
        }
    });
```

**Don't forget:** Change  **dbName** in your **import.html** file to **d3apps3**! 

From within your **d3apps3** folder, push your code into the CouchDB:

```
couchapp push d3apps3
```

Import your data into the CouchDB database by navigating to:

```
http://127.0.0.1:5984/d3apps3/_design/d3apps3/import.html
```

If the import has been successful, the **sp500.csv** file in the **_attachments** folder is no longer needed. If you haven't done so, delete it now. 

That's it. Now your data will be loaded from the CouchDB database.

On your local machine, navigate to

```
http://127.0.0.1:5984/d3apps3/_design/d3apps3/index.html
```

You can watch the result [here](https://rengel.iriscouch.com:6984/d3apps3/_design/d3apps3/index.html).

## Conclusion

If you followed this tutorial, you now should have three CouchDB databases: **d3apps1**, **d3apps2**, **d3apps3**. They demonstrate different degrees of integration of an D3 application into a CouchDB database. The last one (**d3apps3**) has no dependencies on external files whatsoever (no libraries, no data files). Everything is contained in the database. Neither middleware nor a framework is required to access and display the data. The application and the data can be moved around, copied, replicated, deployed, etc. just by applying these operation to the database file. The only requirement is that the recipient has CouchDB running (which is available for all major operating systems).

## Roadmap

This tutorial is the result of about a week of researching and figuring out, how d3 can be integrated with a database. Of course, this is a simple application, and the data is contained in a single document. The application has been taken verbatim from Mick Bostock's example, and no 'real' database features (records, selections, filters, etc.) are used. To show that this is not a toy application, some issues must be solved. It must be shown 
* that one can work with many documents (records). Because I'm interested in (historical) timelines, my target at the moment is around 50,000 to 100,000 documents.
* that one can integrate richer content (pictures, videos, audio files, etc.). There are many applications that use CouchDB to deliver content of this type.
* that one can build a richer user interface. Again, there are many application that feature rich interfaces with CouchDB. 

Stay tuned!

  