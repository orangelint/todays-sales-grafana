## today's sales data

A guide to creating grafana graphs that display current day sales and remaining forecast. 

## assumptions

1)  you have a grafana instance running
2)  data sources that host your sales totals are added to your running grafana instance 

## add a blank graph

after logging into grafana, on left hand side click "+", then "Add new panel" 
<img src="/images/add-blank-graph.png" width=50% height=50%>

grafana will immediately plot some data using its own embedded `default` data source _(just to make you feel good)_   
<img src="/images/default-datasource.png" width=50% height=50%>

## import today's sales into the graph

replace the default datasource with the datasource hosting your sales data. 

  - In our example:  
 ```metrics-frontdoor```


replace the default query with the query that extracts your sales data. 

  - In our example:  
 ```SELECT mean("Stores_Sales_Cafe_Level2") FROM "Task_mips_store" WHERE ("_blossom_id" = 'CI02838708') AND $timeFilter GROUP BY time($__interval) fill(null)```
<img src="/images/widgets.png" width=70% height=70%>


## import today's forecasted sales into the graph

add another query (same datasource) that uses xgboost to forecast the remainder of the day

  - In our example:  
```SELECT FORECAST(mean("Stores_Sales_Cafe_Level2"), 'xgb', 24h, 3) FROM "Task_mips_store" WHERE ("_blossom_id" = 'CI02838708') AND time > now() - 4d GROUP BY time(5m) fill(null)```
<img src="/images/forecast.png" width=70% height=70%>

## label and color the sales datasets

On upper right of your dashboard, expand "Show options" feature and update the following: 

  -Under "Settings", click "show options", add a title to your panel: "WIDGETS"   

  -Under "Display", set "Null value" to "connected"   

  -Under "Series Overrides", add "Change Color" to "widgets" (select white). 

  -Under "Series Overrides", add "Change Color to "forecast (select orange). 

Your sales data now is complete and connected with today's forecast finishing the day
<img src="/images/today.png" width=70% height=70%>

## zoom out your sales data (for funzies!)   

click on the date picker in the upper right hand corner and set timings to 12 hours in past, and 12 hours in future.   
<img src="/images/datepicker.png" width=20% height=20%>

## tada! now you have a 24 hour chart of past and projected sales! 
<img src="/images/24hr.png" width=90% height=90%>

