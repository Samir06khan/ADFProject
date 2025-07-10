
# Azure Data Factory Project: Country & Customer-Product Data Integration

## Overview

This project consists of 4 steps:
1. Fetch country data (India, US, UK, China, Russia) from REST API.
2. Run the pipeline twice daily using triggers (12:00 AM and 12:00 PM IST).
3. Copy customer data to ADLS if record count > 500 and trigger child pipeline if > 600.
4. Pass customer count to child pipeline that copies product data.

## Folder Structure

- `Pipelines/`: Contains JSON definitions for ADF pipelines.
- `Datasets/`: Organized into `HTTP`, `SQL`, and `ADLS` datasets.
- `LinkedServices/`: Connections to REST API, Azure SQL DB, and ADLS.
- `Triggers/`: Trigger to run country pipeline twice a day.
- `Parameters/`: Parameters for inter-pipeline communication.

## How to Use

1. Upload these JSON files into Git-enabled Azure Data Factory.
2. Connect ADF to GitHub repo.
3. Deploy pipelines, linked services, datasets.
4. Publish and run pipelines from ADF Studio.

## Note

This is a GitHub-ready structure. You can upload it to a public/private repo and connect it with Azure Data Factory Studio in Git mode.
