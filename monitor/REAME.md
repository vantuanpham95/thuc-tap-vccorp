## Telegraf -> kafka -> kafka-influxdb -> influxdb -> grafana
    
### Install Telegraf

    ansible-playbook -i hosts site.yml --tags "setup_telegraf"

### Install Kafka-system

    ansible-playbook -i hosts site.yml --tags "setup_kafka"

Cài trên một máy trong cụm server:

        ansible-playbook -i hosts site.yml --tags "setup_kafka_influxdb" --limit servers[0]

### Install InfluxDB

Cài trên 1 máy:

        ansible-playbook -i hosts site.yml --tags "setup_influxdb" --limit servers[0]  

Tạo Database:

        ansible-playbook -i hosts roles/influxdb/create_db.yml  --limit servers[0]

### Install Grafana

    ansible-playbook -i hosts site.yml --tags "setup_grafana" --limit servers[0]

### Run configure kafka-influxdb

- Thực thi trên máy có cài kafka_influxdb 

        cd /opt/pypy-venv/ && python -m kafka_influxdb -c custom-config.yaml -s



