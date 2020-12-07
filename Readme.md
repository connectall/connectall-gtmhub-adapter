# ConnectALL Gtmhub Adapter

ConnectALL Gtmhub Adapter is developed as an extension to the Universal adapter capability of ConnectALL. This adapter specifications will let the user use Gtmhub with Webhooks to read and write the data in to Gtmhub.

Please refer to https://wiki.connectall.com/ca/latest/adapters/universal-adapter for more information

# Usecase

As a user of Gtmhub I would like to synchronize OKR Tasks to Internal Jira or similar project management systems for planning and implementation process.

# How to use

> In order to use the Gtmhub adapter you will need to get the license from ConnectALL sales team. Please reach out to sales@connectall.com for licenses and quotes.

## Import specifications
* Import *-adapter-descriptor.json in to ConnectALL using "Install custom adapter" feature. Customize the descriptor after importing to fit your personal projects
* View the transformation specs and open the transformation spec page
* Choose the operation, adapter type and create draft specifications
* Import the transformation specs of {adaptertype}-{operation}-[request|response]-[groovy|jolt].[groovy|json] into ConnectALL
* Test the specifications and save them as Active

## Define application links
* Create an application link in ConnectALL between Gtmhub and a destination application of your choice
* Navigate to `Configuration -> Connections` screen and create a new connection to Gtmhub like `https://app.us.gtmhub.com` as the endpoint
* In the Entity mapping tab under Advanced Properties choose "Sync Type" as POLL
* Use the below REST API templates for each operation

|Operation|API Method|Template|
|--- | --- | ---|
|QUERY MODIFIED RECORDS|GET|/api/v1/tasks?filter=${pollQuery}|
|READ RECORD BY ID|GET|/api/v1/tasks/${recordId}|
|CREATE RECORD|POST|/api/v1/tasks|
|UPDATE RECORD|PUT|/api/v1/tasks/${recordId}|
