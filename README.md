# Power BI and SQL on-demand
Different scenarios of Power BI uisng the SQL on-demand capability of Azure Synapse Analytics 

Several new features of Azure Synapse Analytics just entered public preview, but for me the most interesting by far is the new [SQL on-demand](https://docs.microsoft.com/en-us/azure/synapse-analytics/sql/on-demand-workspace-overview). In this post I am simply exploring some of the potential scenarios this new capability unlocks. 

As a quick refresher, SQL on-demand is defined by the Microsoft documentation as "SQL on-demand is a query service over the data in your data lake. It enables you to access your data through the following functionalities:
* A familiar T-SQL syntax to query data in place without the need to copy or load data into a specialized store.
* Integrated connectivity via the T-SQL interface that offers a wide range of business intelligence and ad-hoc querying tools, including the most popular drivers."

I will also note that the documentation identifies the logical data warehouse (a relational abstraction on top of raw or disparate data without relocating and transforming data, allowing always up-to-date view of your data) as a suitable scenario for the SQL on-demand, which fits in great with the scenarios below: 

## 1. Power BI datasets directly on top of the data lake 
![Scenario 1 diagram](images/scenario-1.jpg)

<tutorial to follow>

## 2. Power BI 2-part aggregation: cached dataset > SQL on-demand
<insert diagram>

<tutorial to follow>

## 3. Power BI 3-part aggregation: cached dataset > SQL Pool > SQL on-demand
<insert diagram>
  
<tutorial to follow>
  
