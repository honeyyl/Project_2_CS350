# Installing Apache Superset on Windows Subsystem for Linux (WSL)

This guide provides a comprehensive outline for installing Apache Superset on **Windows Subsystem for Linux (WSL)**.

---

## Prerequisites

Before installation, ensure the following are installed on your system:

1. **Windows Subsystem for Linux (WSL)**  
   - WSL version 2 is optimal.  
   - Can also be run on Ubuntu (version 20.04 or later) through a virtual machine.

2. **Python**  
   - Python 3.7 or later should be installed.

3. **Node.js**  
   - Node.js 14.x or higher is required for frontend dependencies.

4. **Pip**  
   - Ensure pip (the Python package manager) is installed.

5. **Visual Studio Code (optional)**  
   - A code editor such as VS Code is recommended for future development.

---

## Installation Steps

### 1. Set Up WSL
- Open PowerShell as Administrator and enable WSL:
    ```bash
    wsl --install
    ```
- Ensure WSL version 2 is selected:
    ```bash
    wsl --set-default-version 2
    ```
- Launch the Linux distribution (e.g., Ubuntu) and complete the setup if needed.

- Verify the Linux environment is fully updated:  
    ```bash
    sudo apt update && sudo apt upgrade -y
    ```

---

### 2. Install Python and Pip
- Install Python and pip (if not already installed) in WSL:
    ```bash
    sudo apt install python3 python3-pip -y
    ```
- Verify the installation:
    ```bash
    python3 --version
    pip3 --version
    ```

---

### 3. Install Node.js
- Install Node.js and npm:
    ```bash
    sudo apt install nodejs npm -y
    ```
- Check the installed versions:
    ```bash
    node -v
    npm -v
    ```

---

### 4. (Optional) Create a Virtual Environment
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

### 5. Install Apache Superset
- Install Apache Superset using pip:
    ```bash
    pip install apache-superset
    ```
- Initialize the Superset database:
    ```bash
    superset db upgrade
    ```
- Create an admin user:
    ```bash
    export FLASK_APP=superset
    superset fab create-admin
    ```
    **Note:** Save these credentials for future use.

- (Optional) Load example dashboards to explore Superset's capabilities:
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
- Log in using the credentials you created in Step 5.

- (Optional) Start the server as a background process:  
    ```bash
    # Using nohup
    nohup superset run -p 8088 --with-threads --reload --debugger &

    # Using screen
    screen -S superset
    superset run -p 8088 --with-threads --reload --debugger
    ```

---

## Monitoring Superset
To confirm Superset is running, use the following command:
```bash
ps aux | grep superset
```

---

## Troubleshooting

### Common Issues

1. **Node.js Version Error:**  
   If you encounter errors during frontend build, update Node.js:
    ```bash
    sudo npm cache clean -f
    sudo npm install -g n
    sudo n stable
    ```

2. **Permission Issues:**  
   Use `sudo` if you encounter permission-related errors during installation.

3. **Port Conflicts:**  
   Ensure port 8088 is not in use by another application.

---

## Cleaning Up and Uninstalling
To remove Superset completely:
1. Uninstall Apache Superset:
    ```bash
    pip uninstall apache-superset
    ```
2. Deactivate and delete the virtual environment (if used):
    ```bash
    deactivate
    rm -rf superset-venv
    ```

---

## Wrapping Up
To stop the server, use `Ctrl+C` in the terminal. Data is persisted locally, so you can restart the server without losing progress:
```bash
superset run -p 8088 --with-threads --reload --debugger
