# Data Engineering Code Interview

## 👋 Hi there

Welcome to the Data Engineering code interview! This small data challenge is designed to test out your skills in python, sql, git, and geospatial data processing. The challenge will go from easy to difficult, there's no preassure to finish all the tasks, so try your best and get as far as you can!

To start this challenge, create a new **private** repo under your github username. We would like you to include all the code, notes, visualizations, and data inside of the repo. You will have **48 hours** to complete this data challenge. Once you are done, please provide read access to your repo by inviting `@SashaWeinstein`, `@mbh329`, `td928`, and `@AmandaDoyle`

> ⚠️ Note: **the repo has to be <ins>private</ins>, otherwise you will be automatically <ins>disqualified</ins>**. Also we will check your commit timestamp to only account for the first 48 hours of coding activities.

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
  - [Task 2: Data Aggregation](#task-2-data-aggregation)
  - [Task 3: Data Visualization](#task-3-data-visualization)
  - [Task 4: Spatial Data Processing](#task-4-spatial-data-processing)
  - [Task 5: SQL](#task-5-sql)
  - [Task 6: Spatial SQL](#task-6-spatial-sql)
- [Resources](#resources)

## Introduction

We love the NYC 311 service and the open data products that come with it. In this challenge, you will use **[311 Service Requests from 2010 to Present](https://data.cityofnewyork.us/Social-Services/311-Service-Requests-from-2010-to-Present/erm2-nwe9)** on NYC Open Data, write an ETL pipeline, and produce some data insight.

This challenge has two parts, a python part with 4 steps and a docker/SQL part with 2 steps. The first part will download files and process them, and the second part will use those same files again. It's our expectation that the logic to perform each step in the first half of this challenge will be written in python.

### Python Task 1: Data Download

First you need to download 311 service request records. Write a python script to pulls data from the NYC Open DataAPI based on two filters. The first filter is on responding agency. The second filter is an integer corresponding to the number of days before the current date (i.e. passing "7" means getting records within the past week).  The script should download the associated service requests to python memory and cache to a .csv.

For example, if a user wanted to get all service request records created in the past five where DSNY is the responding agency, they would pass `DSNY` and `5` as the parameters. 

For this task, we ask that you download all 311 service requests filed the **last seven days** where **HPD** is the responding agency.  Save the data as a csv named `raw.csv` in a folder called `data`. 

*Bonus points* if you 1) allow different parameters to be passed to your script from the command line and/or 2) write a bash script to take command line args and call the python code. If you do any bonus task, demostrate your code is dynamic by downloading and saving a series of csv files each with a different timeframe and responding agency, and programmatically save these files as csvs with a naming convention of your choice.

### Python Task 2: Data Aggregation

Write a process to produce a time series table based on the `data/raw.csv`file we created in **Task 1** that has the following fields:

- `created_date_time`/`created_date`: the timestap of request creation by date and hour OR just date
- `complaint_type`: the type of the complaint
- `count`: the count of service requests by `complaint_type` by `created_date_hour`

Store this table in a csv under the `data` folder with a csv file name of your choice.

*Bonus points* if you can 
- Control the choice of date+hour or just date and control complaint type from the command line
- Make the complaint type breakdown optional and control this behavior from the command line as well
- Store multiple tables that pull from different files you cached in python task 1

### Python Task 3: Data Visualization

Create a multi-line plot to show the total service request counts by `created_date_time` for each `complaint_type`. Make sure you store the image of the plot in the `data` folder as a `.png` file.  

*Bonus points* if your code is reasuable w/r/t different input tables. Show us that it is by saving multiple plots corresponding to the different tables you've cached in python step 2

### Python Task 4: Spatial data processing

At Data Engineering, we enhance datasets with geospatial attributes, such as point locations and administrative boundaries. To help us better understand the data from **Python Task 1**, we would like you to join the initial raw data to an NYC administrive boundary. Then create a choropleth map of the 7 day total count of complaints where `HPD` is the responding agency fot a specific `complaint_type` of your choice.

You need to find a **second geospatial dataset and do a geospatial operation** to assign each call to an area. You can't make a chloropleth of calls by borough, zipcode, community district or city, as that information is already assigned to each record. 

Depending on how you generate the map, you can store the map as a `.png` or `.html` under the `data` folder.  Make sure the map includes a legend and title so that it is self explanatory.

### SQL/Docker Task 1: Build container and load data

We ❤️ SQL and docker! At Data Engineering, we work with database containers a lot and we write a lot of fast and simple ETL pipelines using SQL. In this task, you will:

- Set up POSTGIS container using an image.  [Here](https://registry.hub.docker.com/r/postgis/postgis/) is the one we use.
- Load the `data/raw.csv` into a database and name the table `sample_311`. Make sure this process is captured in a script.
- Perform the same aggregation in **Python Task 2** in SQL and store the results in a table (same name as the corresponding csv file).

### SQL/Docker Task 2: Spatial SQL

A lot of popular databases have geospatial extensions, which makes spatial data processing in SQL super easy to use. In this task you will:

- Load the adminstrative boundary data you used in **Python Task 4** into the database as a spatial table
- Do a spatial join in SQL between `sample_311` and the administrative boundary and add the administrative boundary ID as a column to `sample_311`
- Perform the same aggregation in **Python Task 4** and store the result in a table.

*Bonus points*  export the table with the administrative boundary geometry and complaint count into a shapefile under the `data` folder.  

## Resources

- Reach out to Sasha (aweinstein @ planning.nyc.gov) if you have any questions. We love people who ask questions.
- [PostgreSQL Installation Guide](https://www.postgresql.org/download/)
- [Postgis Docker image](https://registry.hub.docker.com/r/postgis/postgis/)
- [Postgis Installation Guide](https://postgis.net/workshops/postgis-intro/installation.html)
- [DigitalOcean Managed Database](https://www.digitalocean.com/products/managed-databases/)

> DigitalOcean is great if you have a lot of trouble with installation, and it offers 100$ of free credit
