# Project 2 - CS350

## Apache Superset Database Visualization Tool

### Contributors
- Stephanie Myalik
- Honey Love
- Au Sein

--- 

## Project Overview
Apache Superset is an open-source business intelligence web application designed to create and share interactive data visualizations and dashboards. This project involves setting up Apache Superset in a PostgreSQL environment, using it to visualize data, and exploring its main features and limitations. The system will be installed on Windows Subsystem for Linux (WSL) for easier integration with the PostgreSQL database.

## Key Requirements
- **System Installation**: Install Apache Superset on WSL, ensuring compatibility with PostgreSQL.
- **System Characteristics**: Apache Superset allows users to visualize complex data sets, creating intuitive dashboards and providing rich analytics. It supports SQL querying, real-time data access, and many popular databases.
- **Usage**: Utilize Python for interacting with Apache Superset and visualizing data in VS Code. Example use cases include generating reports, creating charts, and exploring trends.
- **Shortcomings**: Assess and document any current limitations or bugs in the system, such as integration difficulties with certain databases or performance concerns with large datasets.
- **Future Plans**: Investigate the plans outlined by Apache Superset developers for future improvements, including new features and enhancements.

## Project Timeline
- **November 11, 2024**: Meet to plan procedure and created project repo. 
- **December 2, 2024**: Divided up respective parts of project.
- **December 4, 2024**: Began working on documentation. 
- **December 9, 2024**: Worked on finalizing research. 
- **December 11, 2024**: Finalizing project for submission.

## System Features and Usage:

1. **Installing Apache Superset on WSL**:
     
     Update system and install necessary dependencies
     ``` bash
     sudo apt-get update
     sudo apt-get install -y python3-pip python3-dev libpq-dev libssl-dev
     ```

     Install Apache Superset using pip
     ``` bash
     pip install apache-superset
     ```

     Initialize the Superset database
     ``` bash
     superset db upgrade
     ```

     Create an admin user
     ``` bash
     export FLASK_APP=superset
     superset fab create-admin
     ```

     Start Superset
     ``` bash
     superset run -p 8088 --with-threads --reload --debugger
     ```

2. **Connecting Apache Superset to PostgreSQL**: (CHANGE TO SQLITE)

     ``` bash
     # Access Superset UI by going to localhost:8088
     # Add a new database connection using the following details:
          # Database: SQLite
          # SQLAlchemy URI: postgresql+psycopg2://sqlite:////PATH//file.db
     ```

3. **Using Apache Superset with Python**:

     ``` bash
     from superset import app, db
     from superset.models.core import Database

     # Example of querying a dataset
     query = """
     SELECT column1, column2
     FROM table_name
     WHERE condition = 'value'
     """
     result = db.session.execute(query)
     ```

4. **Generating Visualizations in Apache Superset:**
   - Users can create pie charts, bar graphs, line charts, and more.
   - To create a new visualization, select a dataset, define the chart type, and customize parameters.

## System Shortcomings:

- **Integration with Non-SQL Databases**: Currently, integration with NoSQL databases like MongoDB is not seamless and requires additional configuration.
- **Performance Issues**: Some users report performance slowdowns when dealing with extremely large datasets or complex queries.
- **Limited Customization**: While Apache Superset offers many visualization options, customization of chart styles and formats can be somewhat limited in certain cases.

## Usage
Scalability, fault tolerance, minimal latency, and compatibility with a range of data models and external tools are some of Superset's primary characteristics.
- SQL databases may be accessed with ease thanks to database connectivity.
- Dashboards & Data Visualization: Adaptable tools for making interactive dashboards and viewing data.
- Semantic Layer: Personalized measurements and dimensions for improved analysis.
- SQL IDE: A powerful SQL editor for preparation and data queries.
- Flexible Extensions: Supports plugins and APIs and integrates with current infrastructure.
- Scalable, cloud-native architecture features asynchronous caching and distributed task management.
## Future Plans

Apache Superset's development roadmap includes the following enhancements:

 - **Improved NoSQL Support**: Better native support for NoSQL databases like MongoDB and Apache Druid.
- **Enhanced Data Caching**: Plans to implement more efficient caching techniques to speed up query performance.
- **Advanced Data Exploration Features**: Adding new features like predictive analytics and machine learning integration.
- **Better Customization Options**: Future versions will offer more extensive customization for visualizations, including advanced styling options for charts.
