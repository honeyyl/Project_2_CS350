# Project 2 - CS350

## Apache Superset Database Visualization Tool

### Contributors
- Stephanie Myalik
- Honey Love
- Au Sein

--- 

## Project Overview
Apache Superset is an open-source business intelligence web application designed to create and share interactive data visualizations and dashboards. This project involves setting up Apache Superset in a SQLite environment and using it to visualize data. The system will be installed on Windows Subsystem for Linux (WSL) for easier integration with the SQLite database.

## Key Requirements
- **System Installation**: Install Apache Superset in WSL, and install necessary dependencies.
- **System Characteristics**: Apache Superset allows users to visualize complex data sets, create dashboards and view analytics. It supports SQL querying, real-time data access, and many popular databases including Postgres and SQLite.
- **Usage**: Utilize Python for interacting with Apache Superset and visualizing data in VS Code. Example use cases include generating reports, creating charts, and exploring trends.
- **Shortcomings**: Assess and document any current limitations or bugs in the system, such as integration difficulties with certain databases or performance concerns with large datasets.
- **Future Plans**: Investigate the plans outlined by Apache Superset developers for future improvements, including new features and enhancements.

## Project Timeline
- **November 11, 2024**: Meet to plan procedure and created project repo. 
- **December 2, 2024**: Divided up respective parts of project.
- **December 4, 2024**: Began working on documentation. 
- **December 9, 2024**: Worked on finalizing research. 
- **December 11, 2024**: Finalizing project for submission.

## System Features and Usage

### Key Setup Instructions
1. **Setting up a Virtual Environment**:
   ```bash
   python3 -m venv superset-venv
   source superset-venv/bin/activate
   ```

2. **Installing Dependencies**:
   ```bash
   pip install apache-superset flask
   export FLASK_APP=superset
   touch superset_config.py
   export SUPERSET_CONFIG_PATH=$(pwd)/superset_config.py
   ```

3. **Configuring Superset**:
   - Generate a secret key:
     ```bash
     openssl rand -base64 42
     ```
   - Update `superset_config.py`:
     ```python
     SECRET_KEY = "your-secret-key"
     PREVENT_UNSAFE_DB_CONNECTIONS = False
     SQLALCHEMY_DATABASE_URI = "sqlite:////YOUR PATH/superset.db"
     ```

4. **Initialize Superset**:
   ```bash
   touch superset.db
   superset db upgrade
   superset fab create-admin
   superset fab create-permissions
   ```

5. **Start Superset**:
   ```bash
   superset run -p 8088 --with-threads --reload --debugger
   ```

6. **Access Superset**: Visit `https://localhost:8088` to log in.

### Connecting and Visualizing Data
1. **Adding the SQLite Database**:
   - Navigate to `Settings` -> `Database Connections` -> `+ Database`.
   - Select SQLite and provide the SQLAlchemy URI:
     ```bash
     sqlite:////YOUR PATH/superset.db
     ```
   - Confirm the connection appears in the database list.

2. **Creating a Dataset from a CSV File**:
   - Use SQLite CLI to create and populate a table:
     ```bash
     sqlite3 /YOUR PATH/Project_2_CS350/usage/superset.db
     CREATE TABLE sales_data (
         Date TEXT,
         Region TEXT,
         Product TEXT,
         Sales INTEGER,
         Profit INTEGER
     );
     .mode csv
     .import /YOUR PATH/Project_2_CS350/usage/sales_data.csv sales_data
     SELECT * FROM sales_data LIMIT 10;
     .exit
     ```

3. **Adding and Using the Dataset**:
   - Navigate to `+` -> `Data` -> `Create Dataset`.
   - Select the database and table (`sales_data`).
   - Click "Create Dataset and Create Chart".

4. **Creating Visualizations**:
   - Select the dataset.
   - Create a pie chart:
     - **Dimension**: `Region`
     - **Metric**: `Sales`, aggregated by `SUM`.
   - Save and customize the chart.

<<<<<<< HEAD
5. **Building Dashboards**:
   - Go to the `Dashboard` tab.
   - Click `+ Dashboard`, drag existing charts, and arrange them as needed.
   - Save the dashboard.
=======
     Start Superset
     ``` bash
     superset run -p 8088 --with-threads --reload --debugger
     ```

2. **Connecting Apache Superset to SQLite**: (CHANGE TO SQLITE)

     ``` bash
     # Access Superset UI by going to localhost:8088
     # Add a new database connection using the following details:
          # Database: SQLite
          # SQLAlchemy URI: sqlite:////PATH//file.db
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
>>>>>>> 17d709d1ccec7f66a040b1d6fc66d268f4f693cc

## System Shortcomings
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
