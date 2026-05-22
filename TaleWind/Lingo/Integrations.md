Process of connecting a website or web app to an external software, system, or database.

Most modern integrations are built using Application Programming Interfaces.
API acts as a secure messenger, allowing your website to request specific info from another software, receive it, and display it to the user.
(The controller in MVC?)
They trigger actions across multiple systems. (order -> update inv in shopify + send tracking data to shipping provider
They prevent users from having to navigate away from the site to complete tasks.

ETL (Extract Transform Load)

Consolidates disparate information into a structured format for analytics.

- Pull raw data from various sources (extract)
- Clean and standardize it (transform)
- Load it into a destination system

**Extract**
- SQL/NoSQL databases
- CRM systems (manages and tracks all interactions with cx)
- APIs
- CSVs, XML, other flat files
**Transform**
- In staging area, raw data is processed:
- (staging area is pre-production environment, near-exact replica of live env)
- (it's a "dress rehearsal". made for testing)
- "Cleaning" - aligning with destination schema
- Removes errors through...
- Data validation
- Filtering
- Sorting
- Aggregating
**Load**
- Transformed data is written into destination system.
- data warehouse
- data lake
- data lakehouse

## Data warehouse / lake / lakehouse

- Dimensional modeling
	- Facts (sales amounts, quantative metrics)
	- Dimensions (descriptive context about those facts)
- Star and Snowflake Schemas
- Schema-on-Write

**Common architecture (Three-Tier)**

**Bottom tier**
- database server where data is loaded and stored
- Amazon Redshift, Google BigQuery
**Middle Tier**
- The Online Analytical Processing (OLAP) server that organizes and processes the data into multidimensional "cubes".
- I think it's just trying to say that it ties facts to their contexts.
- Or sales numbers with descriptive context, for example.
**Top Tier**
- Front-end client layer
- query tools, APIs, Business Intelligence (BI) platforms like Tableau or Power BI.