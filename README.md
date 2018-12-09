#MongoDB Charts

##Setup the Datasets

Download the [airbnb dataset](https://github.com/mongodb/charts-demo/airbnb) and import it into your MongoDB Atlas
cluster. Have a look at the [command line tools](https://docs.atlas.mongodb.com/command-line-tools/)
for directions on how to use `mongoimport` with MongoDB Atlas. The included
dataset is sized to be able to fit into a free M0 cluster on MongoDB Atlas.

##Analysing Airbnb Data

###Add a Data Source
1. With a dataset in place, you'll want to enable Charts for your project. 
2. Select the _Charts_ link on the left-hand side, then select the 
_Activate MongoDB Charts_ button.
3. Add a new data source to your project, choose the Cluster, database and 
collection. For this example, I'll use the `sanFranciscoListingsAndReviews`
collection. Then I'll accept the default permissions.


###Create a Dashboard
1. Go to the *Dashboards* tab
2. Click *New Dashboard*
3. Enter a name and description

###Add Some Charts
Inside the MongoDB Charts dashboard, you'll now add a chart to the dashboard.

####Multi-Series Stacked Bar Chart

Let's locate the neighborhoods in San Francisco that have the most Airbnb
properties and split them out by property type.

1. Select the San Francisco Airbnb (`airbnb.sanFranciscoListingsAndReviews`) dataset as the datasource.
2. For the _Chart Type_ select *Bar/Stacked*.
3. Use the following in the _Encoding_ sections for the chart data:
    * X Axis: `_id`, Count aggregation
    * Y Axis: `address.suburb`
        * Sort By: Aggregated Value, Descending
        * Limit: 30
    *  Series: `property_type`
4. Add a name to the chart, like _Properties by Location_ 

Your chart should look something like:
<img src="https://webassets.mongodb.com/_com_assets/cms/Screen Shot 2018-12-07 at 11.13.16 AM-qtrn51nsjv.png" alt="Properties by Location"/>

---
