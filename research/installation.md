## Installing Apache Superset on WSL for Local Development

Apache Superset can also be set up with a Docker container. For more information, refer to the [official documentation](https://superset.apache.org/docs/installation/installing-superset-using-docker-compose).

This installation prioritizes a local development environment using a flask server.

---

## Prerequisites

Before installation, ensure the following are installed on your system:

1. **Windows Subsystem for Linux (WSL)**
2. **Python 3.7 and Pip**
3. **Node.js**

---

## Installation Steps

---

### 1. Check the versions of your installed software:

    ```bash
    python3 --version
    pip3 --version
    node -v
    npm -v
    ```
    Ensure the versions are current.

---

### 2. Create a Virtual Environment

- Set up a virtual environment to isolate Superset and avoid dependency conflicts:

  ```bash
  # Install virtualenv (if not installed)
  pip install virtualenv

  # Create a virtual environment
  python3 -m venv superset-venv

  # Activate the virtual environment
  source superset-venv/bin/activate
  ```

---

### 3. Install Apache Superset

- Install Apache Superset and Flask using pip, and do some configuration:

  ```bash
  pip install apache-superset flask
  ```

  ```bash
  export FLASK_APP=superset
  ```

  ```bash
  touch superset_config.py
  ```

  ```bash
  export SUPERSET_CONFIG_PATH=$(pwd)/superset_config.py
  ```

### 4. Set a strong SECRET_KEY (required for security):

    1. Generate a strong, random secret key:
       ```bash
       openssl rand -base64 42
       ```
    2. Open the `superset_config.py` file:
       ```bash
       nano ~/superset_config.py
       ```
    3. Add the following line with the generated key:
       ```python
       SECRET_KEY = 'your_generated_secret_key'
       ```
       Replace `'your_generated_secret_key'` with the key you generated.

### 5. Create the Superset database:

    ```bash
    touch superset.db
    superset db upgrade
    ```

- Add the following to the superset_config.py:
  ```bash
  PREVENT_UNSAFE_DB_CONNECTIONS = False
  SQLALCHEMY_DATABASE_URI = "sqlite:////YOUR PATH/superset.db"
  ```

### 6. Create an admin user:

    ```bash
    superset fab create-admin
    ```
    Follow the instructions to create an admin user.

- Then add permissions:
  ```bash
  superset fab create-permissions
  ```

### 7. (Optional) Load example dashboards to explore Superset's capabilities:

    ```bash
    superset load-examples
    ```

---

### 6. Start Apache Superset

- Start the Superset web server:
  ```bash
  superset run -p 8088 --with-threads --reload --debugger
  ```
- Access Superset in your browser at:
  ```
  http://localhost:8088
  ```
- Log in using the credentials you created in Step 6.

---

## Troubleshooting

- You may encounter issues with the path and environment variables. Ensure they are correctly set.
- Issues may be encountered if the secrect key is not set correctly.
- Port conflicts may occur if port 8088 is already in use.

---

## SQLite:

- To use SQLite with Superset, you can connect to the SQLite database using the Superset interface. Further comprehensive instructions for an example setup are included within the setup.md file in the usage folder.

- SQLite is accessed with:
  ```bash
  sqlite3 /YOUR PATH/Project_2_CS350/usage/superset.db
  ```
- You can run queries and create tables in the SQLite database to later visualize in Superset.
- Exit SQLite with:
  ```bash
  .exit
  ```
