# Data Engineering Code Interview

## 👋 Hi there

Welcome to the Data Engineering code interview! This small data challenge is designed to test out your skills in python, sql, git, and geospatial data processing. The challenge will go from easy to difficult.  Try your best and complete as much as you can!

To start this challenge, create a new **private** repo under your github username. We would like you to include all the code, notes, visualizations, and data inside of the repo. You will have **48 hours** to complete this data challenge. Once you are done, please provide read access to your repo by inviting `@damonmcc`, `@fvankrieken` and `@AmandaDoyle`

> ⚠️ Note: **the repo has to be private, otherwise you will be automatically disqualified**. Also we will check your commit timestamp to only account for the first 48 hours of coding activities.

## What we are looking for

Your code interview will be evaluated based on your repo, so make sure all files you have are stored in your repo. Specifically we are looking at:

- **Project scafolding**: How you name, manage, and organize your files.
- **Reproducibility**:
  - Ideally if it runs on your machine, it would also run on mine.
  - Make sure you document any software dependency, and installation process.
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
  - We highly **discourage** lumpped commits.

## Table of Content

- [Introduction](#introduction)
  - [Task 1: Data Download](#task-1-data-download)
  - [Task 2: Data Aggregation](#task-2-data-aggregation-via-python)
  - [Task 3: Data Visualization](#task-3-data-visualization-via-python)
  - [Task 4: Spatial Data Processing](#task-4-spatial-data-processing-via-python)
  - [Task 5: SQL](#task-5-Data-Aggregation-via-SQL)
  - [Task 6: Spatial SQL](#task-6-Spatial-data-processing-via-SQL)
- [Resources](#resources)

## Introduction

We love the NYC 311 service and the open data products that come with it. In this challenge, you will use **[311 Service Requests from 2010 to Present](https://data.cityofnewyork.us/Social-Services/311-Service-Requests-from-2010-to-Present/erm2-nwe9)** on NYC Open Data, write an ETL pipeline, and produce some data insight.

### Task 1: Data Download

Write a script to download all service request records created in the **last week** (7 days) and has **HPD** as the responding agency, and store the data in a csv named `raw.csv` in a folder called `data`.

### Task 2: Data Aggregation via Python

Using a Python script/notebook create a time series table based on the `data/raw.csv` file we created from **Task 1** that has the following fields

- `created_date_hour`: the timestap of request creation by date and hour
- `complaint_type`: the type of the complaint
- `count`: the count of service requests by `complaint_type` by `created_date_hour`

Store this table in a csv under the `data` folder with a csv file name of your choice.

### Task 3: Data Visualization via Python

Using a Python script/notebook create a multi-line plot to show the total service request counts by `created_date_hour` for each `complaint_type`. Make sure you store the image of the plot in the `data` folder as a `.png` file.

### Task 4: Spatial data processing via Python

At Data Engineering, we enhance datasets with geospatial attributes, such as point locations and administrative boundaries. To help us better understand the data from **Task 1**, we would like you to join the initial raw data to the **[2020 NTA (Neighborhood Tabulation Area) boundaries](https://www1.nyc.gov/site/planning/data-maps/open-data/census-download-metadata.page)** and create a choropleth map of 7 day total count by NTA of a specific `complaint_type` of your choice.

Depending on how you generate the map, you can store the map as a `.png` or `.html` under the `data` folder.

### Task 5: Data Aggregation via SQL

We ❤️ SQL! At Data Engineering, we deal with databases a lot and we write a lot of fast and simple ETL pipelines using SQL. In this task, you will:

- Load the `data/raw.csv` into a database of your choice and name the table `sample_311`. Make sure this process is captured in a script.
- Perform the same aggregation in **Task 2** in SQL and store the results in a table (same name as the corresponding csv file).

> Note: Depending on your preference, you can use or [Postgres](https://www.postgresql.org/), which is prefered; however, if you are familiar with [SQLite](https://docs.python.org/3/library/sqlite3.html) (much easier to set up and use), you can use that too.

### Task 6: Spatial data processing via SQL

A lot of popular databases have geospatial extensions, which makes spatial data processing in SQL super easy to use. In this task you will:

- Load the NTA data to the database as a spatial table
- Do a spatial join in SQL between `sample_311` and the NTA table and add a `nta` column to `sample_311`
- Perform the same aggregation in **Task 4** and store the result in a table.
- **Bonus**: export the table with NTA geometry and complaint count into a shapefile under the `data` folder.

> Note: At this point you might notice that spatial software is not as straight forward as a simple `pip install`. If you are stuck with database installation or pacakge installation, you might consider adopting **[docker](https://www.docker.com/)**. Docker has a steep learning curve, so don't waste too much time on it.

### Bonus
If you would like to take your work to the next level you will receive bonus points for doing any of the following.
- Allowing different parameters to be passed to the scripts from the command line and/or writing bash scripts to take command line arguments and call the code.  For example, you can pass the agency value as a parameter when downloading the 311 data.
- Demonstrating your experience working with Docker by building a Docker image and pushing an image with your setup and code to Docker hub and giving the Data Engineering team instructions on how to pull it down and run the code.  This bonus section will be graded on how easily we can access your image and make it work on your machines.
If you do not have time or experience doing these "bonus" tasks that's okay!  These tasks are not required and are an optional addition to the tasks described above.  As a guideline, a strong submission of the core tasks will be weighed more heavily than a poorly completed data challenge with bonuses.

## Resources

- Reach out to Damon (DMcCullough @ planning.nyc.gov) if you have any questions. We love people who ask questions.
- [PostgreSQL Installation Guide](https://www.postgresql.org/download/)
- [Postgis Docker image](https://registry.hub.docker.com/r/postgis/postgis/)
- [Postgis Installation Guide](https://postgis.net/workshops/postgis-intro/installation.html)
- [DigitalOcean Managed Database](https://www.digitalocean.com/products/managed-databases/)

> DigitalOcean is great if you have a lot of trouble with installation, and it offers 100$ of free credit
