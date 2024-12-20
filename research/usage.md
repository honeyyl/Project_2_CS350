# Apache Superset

Apache Superset is an open-source tool for data analysis and visualization. It enables users to create and share interactive dashboards. Designed for business intelligence (BI), it leverages **SQLAlchemy** to support a wide range of databases.

---

## Main Purposes and Characteristics of the System

### Database Connectivity
Superset connects to databases via **SQLAlchemy** and works seamlessly with most SQL-speaking databases. This is inclusive of MySQL, PostgreSQL, SQLite, and others.

### Data Visualization and Dashboards
- Create diverse visualization types, such as charts, graphs, and geospatial representations.  
- Intuitive interface requires no prior coding knowledge.

### Semantic Layer
- Define custom dimensions and metrics for datasets to enhance analytical flexibility.

### SQL IDE
- Includes a powerful SQL editor for writing queries and preparing data.

### Adaptable Extensions
- Integrates with existing infrastructure.  
- Supports custom plugins and APIs for automation.

### Cloud-Native Architecture
Superset is scalable, featuring:
- **Distributed Task Management**  
- **Asynchronous Caching**

---

## Key Features

- **Scalability:** Includes horizontal and vertical scaling.  
- **Data Model:** Supports various query languages or data formats (e.g., SQL, JSON, or bespoke APIs).  
- **Performance:** Offers low latency, fault tolerance, and optimized read/write speeds.  
- **Integration:** Compatible with other ASF projects, programming languages, and tools.  

---

## Usage with SQLite Database

### Example: Use SQLite in Superset to Analyze Sales Data

1. **Create a SQLite Database:**
   ```bash
   sqlite3 sales_data.db

2. **Create tables and add sample data to them:**
   ```bash 
   CREATE TABLE orders (
    id INTEGER PRIMARY KEY,
    order_date TEXT,
    customer_id INTEGER,
    order_value REAL
    );

    CREATE TABLE customers (
    id INTEGER PRIMARY KEY,
    name TEXT,
    region TEXT
    );

    INSERT INTO orders VALUES (1, '2024-01-01', 1, 150.00);
    INSERT INTO orders VALUES (2, '2024-01-02', 2, 200.00);
    INSERT INTO customers VALUES (1, 'John Doe', 'North');
    INSERT INTO customers VALUES (2, 'Jane Smith', 'South');

3. **Connect SQLite to Superset:**
   ```bash 
    - Connect to the SQLite database (sales_data.db) using the Superset interface.

    - Create visualizations, execute queries, and examine the tables.

---
### Python Script to Create SQLite Database and Insert Data

```bash
import sqlite3

# Connect to SQLite database (it will create the database if it doesn't exist)
conn = sqlite3.connect('sales_data.db')
cursor = conn.cursor()

# Create tables
cursor.execute('''
CREATE TABLE IF NOT EXISTS orders (
    id INTEGER PRIMARY KEY,
    order_date TEXT,
    customer_id INTEGER,
    order_value REAL
)
''')

cursor.execute('''
CREATE TABLE IF NOT EXISTS customers (
    id INTEGER PRIMARY KEY,
    name TEXT,
    region TEXT
)
''')

# Insert sample data into the tables
cursor.execute("INSERT INTO orders (id, order_date, customer_id, order_value) VALUES (1, '2024-01-01', 1, 150.00)")
cursor.execute("INSERT INTO orders (id, order_date, customer_id, order_value) VALUES (2, '2024-01-02', 2, 200.00)")
cursor.execute("INSERT INTO customers (id, name, region) VALUES (1, 'John Doe', 'North')")
cursor.execute("INSERT INTO customers (id, name, region) VALUES (2, 'Jane Smith', 'South')")

# Commit the changes and close the connection
conn.commit()

# Verify the inserted data by querying the tables
cursor.execute("SELECT * FROM orders")
print("Orders Table:")
print(cursor.fetchall())

cursor.execute("SELECT * FROM customers")
print("Customers Table:")
print(cursor.fetchall())

# Close the connection
conn.close()
