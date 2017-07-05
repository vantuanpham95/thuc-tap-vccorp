## Telegraf -> kafka -> kafka-influxdb -> influxdb -> grafana
    
### Cài Telegraf

    ansible-playbook -i hosts site.yml --tags "telegraf"

### Triển khai trong cụm kafka

    ansible-playbook -i hosts site.yml --tags "kafka"

### Cài trên một máy trong cụm kafka

    ansible-playbook -i hosts site.yml --tags "kafka_influxdb" --limit servers[0]

Cài InfluxDB

        ansible-playbook -i hosts site.yml --tags "influxdb" --limit servers[0]  

Cài Grafana

        ansible-playbook -i hosts site.yml --tags "grafana" --limit servers[0]

Cài Kapacitor

        ansible-playbook -i hosts site.yml --tags "kapacitor" --limit servers[0]

Chạy configure kafka-influxdb

        cd /opt/pypy-venv/ && python -m kafka_influxdb -c custom-config.yaml -s



