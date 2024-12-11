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

or may have to do: ``flask run -p 8088`` finicky...


http://localhost:8088


will have to alter superset_config.py:
 run: ``openssl rand -base64 42``
 copy and paste into secret_key
 run: ``export SUPERSET_CONFIG_PATH=$(pwd)/superset_config.py``


 run: ``superset fab create-admin`` and follow the prompts

then bring the server back up 


you should then be able to log in and view the dashboard

might run into permissions issues: ``superset fab create-permissions``