# Data Engineering Code Interview

## 👋 Hi there

Welcome to the Data Engineering code interview! This small data challenge is designed to test out your skills in Python, SQL, git, and geospatial data processing. The challenge will go from easy to difficult, there's no preassure to finish all the tasks, so try your best and get as far as you can!

To start this challenge, create a new **private** repo under your github username. We would like you to include all the code, notes, visualizations, and data inside of the repo. You will have **48 hours** to complete this data challenge. Once you are done, please provide read access to your repo by inviting `@alexrichey`, `@sf-dcp` and `@AmandaDoyle`

> ⚠️ Note: **the repo has to be private, otherwise you will be automatically disqualified**.

## What we are looking for

Your code will be evaluated based on your repo, so make sure all files are checked in. Specifically we are looking at:

- **Project scafolding**: How you name, manage, and organize your files.
- **Reproducibility**:
  - Ideally if it runs on your machine, it would also run on mine. We would recommend that you use Docker.
  - Make sure you document any installation steps or software dependencies,
- **Code**:
  - Clean
  - Readable
  - DRY (Don't Repeat Yourself)
- **Documentation**:
  - A comprehensive `README.md` on anything that we should know about this repo.
  - Clear instructions on commands to run code and what to expect.
  - Clear documentation for functions/processes in code.
- **Project Management**:
  - We want to see how you manage a multi-part project and how you break down the tasks.
  - Feel free to open up issues for yourself / make pull requests and etc so that your code progress is captured and documented.

## Table of Content

- [Data Engineering Code Interview](#data-engineering-code-interview)
  - [👋 Hi there](#-hi-there)
  - [What we are looking for](#what-we-are-looking-for)
  - [Table of Content](#table-of-content)
  - [Introduction](#introduction)
    - [Task 1: Data Ingestion](#task-1-data-ingestion)
    - [Task 2: Data Aggregation](#task-2-data-aggregation)
    - [Task 3: Spatial SQL](#task-3-spatial-sql)
    - [Task 4: Data Visualization](#task-4-data-visualization)
  - [Resources](#resources)

## Introduction

We love the NYC 311 service and the Open Data products that come with it. In this challenge, you will use two datasets to write an ETL pipeline, and produce some data insight:
- **[311 Service Requests from 2010 to Present](https://data.cityofnewyork.us/Social-Services/311-Service-Requests-from-2010-to-Present/erm2-nwe9)** on NYC Open Data, 
- The Department of City Planning's [2020 Neighborhood Tabulation Areas (NTAs)](https://www.nyc.gov/site/planning/data-maps/open-data/census-download-metadata.page)


### Task 1: Data Ingestion

Write a Python module to download all 311 Service Request records created in the **last week** (7 days) that have **HPD** as the responding agency, and store the data in a PostGIS table called `sample_311`.

Write another module to download the latest version of the Department of City Planning's 2020 Neighborhood Tabulation Areas (NTAs), and store the data in a PostGIS table called `ntas_2020`.

Please also store the raw data in a folder called `data` in the root of the repo.

### Task 2: Data Aggregation

Create a time series table of the 311 complaints with the following columns:
- `created_date_hour`: the timestap of request creation by date and hour
- `complaint_type`: the type of the complaint
- `count`: the count of service requests by `complaint_type` by `created_date_hour`

Export this table to a csv under the `data` folder with a csv file name of your choice.


### Task 3: Spatial SQL

At Data Engineering, we enhance datasets with geospatial attributes, such as point locations and administrative boundaries. To help us better understand the data from the previous tasks, we would like you to determine the 2020 NTA for each `sample_311` Service Request, and create a query that shows total Service Requests counts for the seven day period, grouped by the NTA. This query should include the NTA Name and geometry.

Store the query result in database and export this data into a shapefile under the `data` folder.


### Task 4: Data Visualization

In Python, query your database and create the following visualizations: 
1. Create a multi-line plot to show the total service request counts by `created_date_hour` for each `complaint_type`. Make sure you store the image of the plot in the `data` folder as a `.png` file.
2. and create a choropleth map of 7 day total count by NTA of a specific `complaint_type` of your choice. Depending on how you generate the map, you can store the map as a `.png` or `.html` under the `data` folder.


## Resources
- Reach out to Alex (arichey@planning.nyc.gov) and Sasha (OFilippova@planning.nyc.gov) if you have any questions.
- [PostgreSQL Installation Guide](https://www.postgresql.org/download/)
- [Postgis Docker image](https://registry.hub.docker.com/r/postgis/postgis/)
- [Postgis Installation Guide](https://postgis.net/workshops/postgis-intro/installation.html)
