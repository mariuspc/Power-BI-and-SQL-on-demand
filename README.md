# Power BI and SQL on-demand
Different scenarios of Power BI uisng the SQL on-demand capability of Azure Synapse Analytics 

Several new features of Azure Synapse Analytics just entered public preview, but for me the most interesting by far is the new [SQL on-demand](https://docs.microsoft.com/en-us/azure/synapse-analytics/sql/on-demand-workspace-overview). In this post I am simply exploring some of the potential scenarios this new capability unlocks. 

As a quick refresher, SQL on-demand is defined by the Microsoft documentation as "SQL on-demand is a query service over the data in your data lake. It enables you to access your data through the following functionalities:
* A familiar T-SQL syntax to query data in place without the need to copy or load data into a specialized store.
* Integrated connectivity via the T-SQL interface that offers a wide range of business intelligence and ad-hoc querying tools, including the most popular drivers."

I will also note that the documentation identifies the logical data warehouse (a relational abstraction on top of raw or disparate data without relocating and transforming data, allowing always up-to-date view of your data) as a suitable scenario for the SQL on-demand, which fits in great with the scenarios below: 

## 1. Power BI datasets directly on top of the data lake 
![Scenario 1 diagram](images/scenario-1.JPG)

Refresh a Power BI dataset directly from the data lake, using SQL on-demand. This scenario does not need a pre-provisioned SQL Pool (previously known as SQL Data Warehouse) and relies on the SQL on-demand query service for the compute needed to refresh the Power BI dataset. 

**Step 1**: create an Azure Synapse Analytics workspace. As the SQL on-demand feature is still in preview at the time of this writing, make sure you select the Azure Synapse Analytics (workspace preview) version.

**Step 2**: launch Synapse Studio.

![Synapse Studio](images/synapseStudio.JPG)

**Step 3**: using the SQL on-demand engine, create a view over data stored in the udnerlying data lake. In this example, I am creating a view called vPopulation in a database called onDemandDB, exposing population data from a sample storage account. If you want to follow along, or get more details on how this is done, please follow [this tutorial] (https://docs.microsoft.com/en-us/azure/synapse-analytics/sql/query-single-csv-file)(also make sure to also run the setup script in the tutorial).

![view population](images/vPopulation.JPG)
  
**Step 4**: go back to the Overview blade of your Synapse Workspace (in the Azure portal, outside of the Synapse Studio), and note down the name of the SQL on-demand endpoint. 

![SQL on-demand endpoint](images/SQLondemandEndpoint.JPG)

**Step 5**: start Power BI Desktop and create a connection to Azure SQL Database. Enter the SQL on-demand endpoint name as the server name, then the database name and Import as the connectivity option.

![connect from Power BI](images/PBI-connect.JPG)

**Step 6**: once you enter the correct authentication, you should see all the views and tables available in the on demand database, including vPopulation in this case.

![vPopulation](images/PBI-vPopulation.JPG)

**Step 7**: build a Power BI report on top of the imported data and publish it to the Power Bi service 

**Step 8**: schedule a refresh for the dataset 

![scheduled refresh](images/PBI-scheduledRefresh.JPG)



## 2. Power BI 2-part aggregation: cached dataset > SQL on-demand
![Scenario 2 diagram](images/scenario-2.JPG)

<tutorial to follow>

## 3. Power BI 3-part aggregation: cached dataset > SQL Pool > SQL on-demand
![Scenario 3 diagram](images/scenario-3.JPG)
  
<tutorial to follow>
  
