# Open Market Benefits Reconciliation Tool

Ana Gutierrez product owner for open market benefits reconciliaton tool

Olivia Ruppert point of contact

- Bills format change time to time from senders

- In which repository are the invoices currently stored? Are they distributed across multiple repositories?

- How do the invoices get submitted or received?

- Are there any specific indicators or red flags to watch for when comparing the invoices to the spreadsheet that could signal data inconsistencies?

Business Deep Dive session: CODE MAPPING INTEGRATION ASSISTANT
- these are codes uses in prism system, each cliente create its own codes for payments, benefits, vacation, full time, parttime etc. Codes will last in client side and needs to be mapping with centralized codes
- 

UNIVERSAL DATA CONSOLIDATION PROJECT
- Prism no quiere que vensure vea los clientes de sus clientes
- 

Monthly sensus automation
- https://api-docs.prismhr.com/
- integrating spreedsheet
- maping technique
- validation data technique
- governance to hide sensitive data before entering to fabric and while in fabric
- 

api to db
api to excel
excel to excel
smartsheet to excel
files to db
excel to db

- crear un standard de nombres


- client behavior analisys
- esta gene usa clientspace
- predicttive analysis for sentiment, check how people is writing in the cases
- clients mark as a risk
- clients on rick needs to be analyze, talk with the accoutn manager, and the sucess team of the client
- answering questions and making dashboard analysis by AI, making analysis over reports because is hard to watch out all the data in the reports

Filters
- region based
- industry types
- client specific filters
- case types filters
- links on prism and client space is important to have them in the data
- share views / powerbi


Meeting with Daniel Arledge, existing data PROJECT
- user data consolidation projects
- client consolidation effort, they have several projects
- taking leverage in snowflake and prism
- there is a warehouse call client360, feed it in azure datalake, still intro stages, still lot of to do, pretty much prism data
- they have other projects made in fabric pero no lo explotan mucho
- sheetal edrington, se une a la llamada to clarify what they are doing that might be our interest
- fabric they used to play a bit with fabric data flows and make some sql on it}
- sheetal, the most difficult is to get all the data from the different sources and systems
- actually she suggest to export data to csv
- put a list together of all the payrole platforms, get the best way to get such data, understand what kind of data you get before
- she suggest the best for the Ai projects is to use client360
- both difficult access the credentials and the diversity of the data
- the easy way is to access the snowflake
- clientspace maybe melissa can help us to get access
- in snowflake like 30 tables with 6 millions records, sam knows better
- 