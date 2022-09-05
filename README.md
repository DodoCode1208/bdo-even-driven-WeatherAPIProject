# bdo-even-driven-WeatherAPIProject
Contains a project developed on event driven architecture (Weather API)

**Problem Description : **
1. Requirement is to fetch the weather/climate information on dynamic basis from a public api (OpenWeather api). 
2. The data should be stored somewhere once fetched from external source (in json) and a clean up should be performed on the weather data to remove unwanted data (Or Correction of data type formats).
3. Once weather data is transformed should be stored in a separate system which can be utilized on a distributed level by different client facing systems.
4. Once data is transormed should be available to multiple client systems for consumption in an event driven architecture.
5. Different systems should model the open api data according to their needs and store it in separate storage (specific to usage).

Client UseCase - Client use case can be to create a react application (an application to Order beverages) which utilizes the weather information or params and displays the mood and coffee suggestions. (Frontend - Out of Scope)

**Targeted Solution: **
1. Use serverless functions (Azure) to periodically call "**OpenWeather**" API in order to fetch and dump weather data in json format to a blob storage.
2. Use another serverless function (Azure) to trigger on blob creation as part of step 01 and in sequence runs the logic to transform the raw json data for clean up and provide a consumable json data as per needs.
3. Store the transformed data in another blob storage and which indirectly works as a publisher to an event grid system.
4. Create topic under Event Grid : Source : Blob Type , Operation : Insert 
5. Create a Subscription to consume the topic and thus trigger an http post request towards a web hook (Azure function / a web api) which models the data and store it in SQL storage for further consumption by client system.

**Technology Stack Used**

1. .NET 6 
2. .NET 6 Web Api (Lightweight api - Minimum build)
3. Azure Function
4. Azure Event Grid
5. Dependency Injection via .NET 6 
6. Azure SQL Server
7. Postman






