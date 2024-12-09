``python3 -m venv superset-venv``

``source superset-venv/bin/activate``

``pip install apache-superset``

``export FLASK_APP=superset``

``pip install flask``

``touch superset_config.py``

``export SUPERSET_CONFIG_PATH=$(pwd)/superset_config.py``

verify: ``superset export_config``

``touch /home/stmyalik/CS350/Project_2_CS350/usage/superset.db``

``superset db upgrade``

``superset export_config``

``superset run -p 8088 --with-threads --reload --debugger``

http://localhost:8088

