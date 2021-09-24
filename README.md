## today's sales data

A guide to creating grafana graphs that display today's sales

## assumptions

1)  you have a grafana instance running
2)  data sources that host your sales totals are added to your running grafana instance 

## add a blank graph

after logging into grafana, on left hand side click "+", then "Add new panel" 
<img src="/images/add-blank-graph.png" width=50% height=50%>

grafana will immediately plot some data using its own embedded default data source _(just to make you feel good)_
<img src="/images/default-datasource.png" width=50% height=50%>

## import today's sales into the graph

select the datasource that hosts your sales data. In our example, the datasource is named `metrics-frontdoor`
<img src="/images/widgets.png" width=50% height=50%>


## import today's forecasted sales into the graph

## label and color the sales datasets

## zoom out your sales data (for funzies!) 

