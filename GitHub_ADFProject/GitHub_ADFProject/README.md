
##  Pipelines

### 1. `GetCountryData_Pipeline`
- Fetches data for 5 countries (India, US, UK, China, Russia) from:  
  `https://restcountries.com/v3.1/name/{country}`
- Saves as JSON to Azure Data Lake with the file name equal to the country name.

### 2. `CustomerData_MainPipeline`
- Queries a count of customer records.
- If count > 500, copies customer data to ADLS.
- If count > 600, triggers the child pipeline and passes the customer count.

### 3. `ProductData_ChildPipeline`
- Accepts `customer_count` as a parameter.
- Copies product data from SQL to ADLS only if the parameter value > 600.


---
## Datasets

### HTTP Datasets
- **Country_REST_API_Dataset.json**  
  Dataset for dynamic REST API call using `{CountryName}` as parameter.

### ADLS Datasets
- **Country_JSON_Output_Dataset.json**  
  Output dataset for storing each country's JSON file.
- **Customer_JSON_Output_Dataset.json**  
  Output dataset for customer data if count > 500.
- **Product_JSON_Output_Dataset.json**  
  Output dataset for product data from child pipeline.

### SQL Datasets
- **Customer_SQLTable_Dataset.json**  
  Source SQL dataset for customer table.
- **Product_SQLTable_Dataset.json**  
  Source SQL dataset for product table.

---

##  Linked Services

- **AzureSQL_DB_LinkedService.json**  
  Connection to Azure SQL Database (provide server, DB name, auth).
  
- **ADLS_LinkedService.json**  
  Connects to Azure Data Lake Storage Gen2 using managed identity or key.
  
- **REST_CountryAPI_LinkedService.json**  
  Defines base URL for REST API: `https://restcountries.com`.

---

##  Triggers

- **CountryData_DailyTrigger.json**
  - Runs `GetCountryData_Pipeline` automatically at:
    - 12:00 AM IST
    - 12:00 PM IST

---

## Parameters

- **ProductData_ChildPipeline_Params.json**
  - Defines `customerCount` parameter passed from parent to child pipeline.

---

## Technologies Used

- Azure Data Factory
- Azure SQL Database
- Azure Data Lake Storage Gen2
- REST API: https://restcountries.com
- GitHub (for repository integration)

---

## Instructions to Use

1. Import all JSON files into Azure Data Factory via GitHub-connected repo or manually via ADF Studio.
2. Configure Linked Services with your actual credentials for SQL, ADLS, and REST.
3. Publish all changes.
4. Monitor the trigger and debug pipelines for testing.

---

##  Author

**Intern Name**: *Samir Khan*   

---
