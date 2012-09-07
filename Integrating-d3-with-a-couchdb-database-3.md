## Accessing data in a CouchDB database from a D3 application

To access the data in your **d3apps** CouchDB, you need to change your **index.html** file. At the beginning you must insert two **jquery** scripts:

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
    $.couch.db("d3apps").openDoc("sp500", {
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

From within your **d3apps** folder, push your code into the CouchDB:

```
couchapp push d3apps
```

That's it. Now D3 will load the data from the CouchDB database.
