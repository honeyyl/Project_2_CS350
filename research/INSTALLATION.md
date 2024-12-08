## Installation of Apache Superset

This is an outline for installing Apache Superset on **Windows Subsystem for Linux (WSL)**.

## Prerequisites

Before installation, ensure the following are installed on your system:

1. **Windows Subsystem for Linux (WSL)**
    - WSL version 2 is optimal.
    - Can also be ran on Ubuntu (version 20.04 or later) through a virutal machine. 

2. **Python**
    - Python 3.7 or later should be installed. 

3. **Node.js**
    - Node.js 14.x or higher is required for frontend dependencies.
  
4. **Pip**  
   - Ensure pip (the Python package manager) is installed. 

5. **Visual Studio Code (optional)**
   - A code editor such as VS Code is recommended for future development. 

## Installation Steps

1. **Setup Up WSL**
- Open PowerShell as Administrator and enable WSL. (command below to install)
``` bash
wsl --install
```
- Ensure WSL version 2 is selected.
``` bash
wsl --set-default-version 2
```