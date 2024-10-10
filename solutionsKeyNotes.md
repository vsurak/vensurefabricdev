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


# Arquitectura Vensure Meeting

## del diagrama general que había hecho Leo antes
- sources: external websites laws y regulations, salesforce, docs en onedrive, plexity, pdf, excels
- outputs: snowflake, clientspace sql

## Oscar Esau 

### automatic client inbound process 
- para este punto no estarían ocupando integrar nada con onelake.

## david cermeno - 
### M&A + inbound employee benefits analysis tool 
- FE en angular que deposita files en por medio de azure functions
- entran archivos directamente en onelake, son pdf, csv y excel
- spike para saber si openai o azure documents Ai
- de la AI meten a data warehouse de onelake
- desde warehouse es donde crean las salidas

### monthly census automation
- subida de files a onelake
- se dispara que se subio un file y eso dispara un pipeline
- ese pipeline llama a la AI que podria ser chatgpt o el de azure
- se manda un email
- el pipeline manda a prism y tambien ocupa leer de prism
- el pipeline manda y escribe a warehouse
- asumen que se extrae la info de prism por api
- el mismo pipeline mete y saca info del datawarehouse
- version de skateboard iba a ser consumir puro excel
- 

## mauricio araneda
### tax jurisdiction monitor
- aun non tienen claridad de donde sale la info para el proyecto

### code mapping integration assistant
- quieren tomar info del api de prism, son 4 fuentes diferentes del mismo api
- para meter en onelike ocupan parametros, setup de algun maping con AI que lo harian con un .net funcion service, o sea van a crear un api
- de onelake debe salir el codemaping para tener codigos unificados, este formato de tabla lo tienen claro
- 

## adolfo alcaraz
### client employer assignment optimizer
- fuentes prismhr, clientspace crm, UI y saca unstructured data
- hay data semiestructurada
- la info debe ser cargada en onelake 
- esto va a ser consumido por powerbi
- la no estructurada puede ser leyes y cosas textuales

## nicolas locatti
### Ai virtual assistant for SMB WSE guidance and support
- ingesta de documentos para un bot, esos documentos entran por onelake y serían en flat
- ingesta por web scrapping, pdf
- hay documentacion que tienen solo en videos hay que hacer transcribe

## andres mora
### sales dashboard
- este va a quedar pendiente 

### client behavior analysis
- clientspace api o azure sql, alguna de esas fuentes y de ahi pasa a onelake
- synapse analytics para sacar la info y de ahi pasa a synapse data warehousing
- 


==================================

hay varias salidas de powerbi, se va a ocupar cierto nivel de permisos en los datos aunque sea mínimo

