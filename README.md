## today's sales data

A guide to creating grafana graphs that display today's sales

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
 ```SELECT FORECAST(mean("Stores_Sales_Cafe_Level2"), 'xgb', 24h, 3) FROM "Task_mips_store" WHERE ("_blossom_id" = 'CI02838708') AND time > now() - 4d GROUP BY time(5m) fill(null)```
<img src="/images/forecast.png" width=70% height=70%>


## import today's forecasted sales into the graph

add another query (same datasource) that uses xgboost to forecast the remainder of the day

  - In our example:  
```
<img src="/images/forecast.png" width=50% height=50%>

## label and color the sales datasets

## zoom out your sales data (for funzies!) 

