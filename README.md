# Data Engineering Code Interview

## 👋 Hi there

Welcome to the Data Engineering code interview! This small data challenge is designed to test out your skills in Python, SQL, git, and geospatial data processing. The challenge will go from easy to difficult so try your best and get as far as you can!

To start this challenge, create a new **private** repo under your GitHub username. We would like you to include all the code, notes, visualizations, and data inside of the repo. You will have **48 hours** to complete this data challenge. Once you are done, please provide read access to your repo by inviting `@damonmcc` and `@alexrichey`.

> [!WARNING]
> **Your repo has to be private, otherwise you will be automatically disqualified**.

## What we are looking for

Your code will be evaluated based on your repo, so make sure all files are checked in. Specifically we are looking at:

- **Project scaffolding**:
  - How you name, manage, and organize your files.
- **Reproducibility**:
  - Ideally if it runs on your machine, it would also run on ours.
  - Make sure you document any installation steps or software dependencies.
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
  - Feel free to open up issues for yourself and/or make pull requests so that your code progress is captured and documented.

## Table of Contents

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

We love the NYC 311 service and the Open Data products that come with it. In this challenge, you will use two datasets to write a data pipeline, and produce some insights:
- **[311 Service Requests from 2010 to Present](https://data.cityofnewyork.us/Social-Services/311-Service-Requests-from-2010-to-Present/erm2-nwe9)** on NYC Open Data
- The Department of City Planning's [2020 Neighborhood Tabulation Areas (NTAs)](https://www.nyc.gov/site/planning/data-maps/open-data/census-download-metadata.page)


### Task 1: Data Ingestion

Write a Python module to download all 311 Service Request records created in the **last week** (7 days) that have **HPD** as the responding agency, and store the data in a PostGIS table called `sample_311`.

Write another module to download the latest version of the Department of City Planning's 2020 Neighborhood Tabulation Areas (NTAs), and store the data in a PostGIS table called `ntas_2020`.

Please also store the raw data in a folder called `data` in the root of the repo.

### Task 2: Data Aggregation

Create a time series table of the 311 complaints with the following columns:
- `created_date_hour`: the timestamp of request creation by date and hour
- `complaint_type`: the type of the complaint
- `count`: the count of service requests by `complaint_type` by `created_date_hour`

Export this table to a csv under the `data` folder with a csv file name of your choice.

### Task 3: Spatial SQL

At Data Engineering, we enhance datasets with geospatial attributes, such as point locations and administrative boundaries. To help us better understand the data from the previous tasks, we would like you to use SQL to determine the 2020 NTA for each `sample_311` Service Request, and create a query that shows total Service Requests counts for the 7-day window ingested in Task 1 grouped by the NTA. This query should include the NTA Name and geometry.

Store the query result in the database and export this data as a shapefile under the `data` folder.

> [!NOTE]
> We use [Postgres](https://www.postgresql.org/) and [DuckDB](https://duckdb.org/docs/current/).

### Task 4: Data Visualization

In Python, query your database and create the following visualizations:
1. Create a multi-line plot to show the total service request counts by `created_date_hour` for each `complaint_type`. Make sure you store the image of the plot in the `data` folder as a `.png` file.
2. Create a choropleth map of 7 day total count by NTA of a specific `complaint_type` of your choice. Depending on how you generate the map, you can store the map as a `.png` or `.html` under the `data` folder.

### Bonus

If you would like to take your work to the next level you will receive bonus points for doing any of the following.

- Allowing different parameters to be passed to the scripts from the command line and/or writing bash scripts to take command line arguments and call the code. For example, you can pass the agency value as a parameter when downloading the 311 data.
- Demonstrating your experience working with Docker by building a Docker image and pushing an image with your setup and code to Docker hub and giving the Data Engineering team instructions on how to pull it down and run the code. This bonus section will be graded on how easily we can access your image and make it work on our machines.

> [!NOTE]
> If you don't have time for these "bonus" tasks that's okay! These tasks are not required and are an optional addition to the tasks described above. As a guideline, a strong submission of the core tasks will be weighed more heavily than a poorly completed one with bonuses.

## Resources

- Reach out to your Department of City Planning contact if you have any questions.
- [PostgreSQL Installation Guide](https://www.postgresql.org/download/)
- [Postgis Docker image](https://registry.hub.docker.com/r/postgis/postgis/)
- [Postgis Installation Guide](https://postgis.net/workshops/postgis-intro/installation.html)
