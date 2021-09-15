# Data Engineering Code Interview

## 👋 Hi there

Welcome to the Data Engineering code interview! This small data challenge is designed to test out your skills in python, sql, git, and geospatial data processing. The challenge will go from easy to difficult, there's no preassure to finish all the tasks, so try your best and get as far as you can!

To start this challenge, create a new **private** repo under your github username. We would like you to include all the code, notes, visualizations, and data inside of the repo. You will have **48 hours** to complete this data challenge.

> ⚠️ Note: **the repo has to be <ins>private</ins>, otherwise you will be automatically <ins>disqualified</ins>**. Also we will check your commit timestamp to only account for the first 48 hours of coding activities.

## What we are looking for

Your code interview will be evaluated based on your repo, so make sure all files you have are stored in your repo. Specifically we are looking at:

- **Project scafolding**: how you name, manage, and organize your files.
- **Reproducibility**:
  - Ideally if it runs on your machine, it would also run on mine.
  - make sure you document any software dependency, and installation process.
- **Code**:
  - clean
  - readable
  - DRY (Don't Repeat Yourself)
- **Documentation**:
  - A comprehensive `README.md` on anything that we should know about this repo.
  - clear instructions on commands to run code and what to expect.
  - clear documentation for functions/processes in code.
- **Project Management**:
  - We want to see how you manage a multi-part project and how you break down the tasks.
  - Feel free to open up issues for yourself / make pull requests and etc so that your code progress is captured and documented.
  - we highly **discourage** lumpped commits.

## Table of Content

- [Introduction](#introduction)
  - [Task 1: Download data](#task-1-download-data)
  - [Task 2: Data Aggregation](#task-2-data-aggregation)
  - [Task 3: Data Visualization](#task-3-data-visualization)
  - [Task 4: Spatial Data Processing](#task-4-spatial-data-processing)
  - [Task 5: SQL](#task-5-sql)
  - [Task 6: Spatial SQL](#task-6-spatial-sql)
- [Resources](#resources)

## Introduction

We love the NYC 311 service and the open data products that come with it. In this challenge, you will use **[311 Service Requests from 2010 to Present](https://data.cityofnewyork.us/Social-Services/311-Service-Requests-from-2010-to-Present/erm2-nwe9)** on NYC Open Data, write an ETL pipeline and produce some data insight.

### Task 1: Download data

Write a python script/notebook to download all service requests openned last week (7 days) and store the data in a csv named `raw.csv` in a folder called `data`.

### Task 2: Data Aggregation

Create a time series table based on the `data/raw.csv` file we created from **Task 1** that has the following fields

- `created_date_hour`: the timestap of request creation by date and hour
- `complaint_type`: the type of the complaint
- `count`: the count of service requests by `complaint_type` by `created_date_hour`

Store this table in a csv under the `data` folder with a csv file name of your choice.

### Task 3: Data Visualization

Create a multi-line plot to show the total service request counts by `created_date_hour` for each `complaint_type`. Make sure you store the image of the plot in the `data` folder as a `.png` file.  

### Task 4: Spatial Data Processing

At Data Engineering, we enhance the dataset with useful geospatial attributes, such as adding point location, adding administrative boundaries. To help us better understand the data from **Task 1**, we would like you to join the initial raw data to the **[2020 NTA (Neighborhood Tabulation Area) boundaries](https://www1.nyc.gov/site/planning/data-maps/open-data/census-download-metadata.page)** and create a choropleth map of 7 day total count by NTA of a specific `complaint_type` of your choice.

Depends on how you generate the map, you can store the map as a `.png` or `.html` under the `data` folder.

### Task 5: SQL

We ❤️ SQL! At Data Engineering, we deal with databases a lot and we write a lot of fast and simple ETL pipelines using SQL. In this task, you will:

- load the `data/raw.csv` into a database of your choice, name the table `sample_311`, make sure this process is captured in a script.
- perform the same aggregation in **Task 2** in SQL and store the results in a table (same name as the corresponding csv file)

> Note: Depends on your preference, you can use or [Postgres](https://www.postgresql.org/) is prefered, however, if you are familiar with [SQLite](https://docs.python.org/3/library/sqlite3.html) (much easier to set up and use), you can use it too.

### Task 6: Spatial SQL

A lot of popular databases have geospatial extensions, which makes spatial data processing in SQL super easy to use. In this task you will:

- load the NTA data to the database as a spatial table
- do a spatial join in SQL between `sample_311` and the NTA table and add a `nta` column to `sample_311`
- perform the same aggregation in **Task 4** and store the result in a table.
- **Bonus**: export the table with NTA geometry and complaint count into a shapefile under the `data` folder.  

> Note: At this point you might notice that spatial software is not as straight forward as a simple `pip install`, If you are stuck with database installation or pacakge installation, you might consider adopting **[docker](https://www.docker.com/)**. Docker has a steep learning curve, so don't waste too much time on it.

## Resources

- Reach out to me (bcao @ planning.nyc.gov) if you have any questions, we love people who ask questions.
- [PostgreSQL Installation Guide](https://www.postgresql.org/download/)
- [Postgis Docker image](https://registry.hub.docker.com/r/postgis/postgis/)
- [Postgis Installation Guide](https://postgis.net/workshops/postgis-intro/installation.html)
- [DigitalOcean Managed Database](https://www.digitalocean.com/products/managed-databases/)

> DigitalOcean is great if you have a lot of trouble with installation, and it offers 100$ of free credit
