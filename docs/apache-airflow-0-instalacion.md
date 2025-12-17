# 🍀 Apache Airflow &mdash; 🧾 Instalación

![Logo Apache Airflow](images/airflow/wordmark_2.svg#derecha "Logo Apache Airflow")

Programa e monitoriza fluxos de datos. Unha especie de cron con esteroides ou un orquestador de datos.

## Instalación en GNU/Linux Debian/Ubunt/Mint

``` bash
mkdir $HOME/airflow
cd $HOME/airflow
curl -LfO 'https://airflow.apache.org/docs/apache-airflow/3.1.1/docker-compose.yaml'
mkdir -p ./dags ./logs ./plugins ./config
echo -e "AIRFLOW_UID=$(id -u)" > .env
docker compose run airflow-cli airflow config list
docker compose up airflow-init
docker compose up
curl -LfO 'https://airflow.apache.org/docs/apache-airflow/3.1.1/airflow.sh'
chmod +x airflow.sh
```


## Máis información:

- <https://airflow.apache.org/>
- <https://airflow.apache.org/docs/apache-airflow/stable/howto/docker-compose/index.html>
- <https://github.com/javicacheiro/pyspark_course/tree/master/supplementary/airflow>
- <https://aitor-medrano.github.io/iabd/dataflow/airflow.html>