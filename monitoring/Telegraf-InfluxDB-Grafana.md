## Install Telegraf + InfluxDB + Grafana on Ubuntu 16.04

### Install InfluxDB
	wget https://dl.influxdata.com/influxdb/releases/influxdb_1.2.4_amd64.deb
	sudo dpkg -i influxdb_1.2.4_amd64.deb

- Khởi động
	
		sudo systemctl start influxdb.service

- Tạo CSDL

		influx
		create datase telegraf
		show databases

### Install Grafana 
	wget https://s3-us-west-2.amazonaws.com/grafana-releases/release/grafana_4.2.0_amd64.deb
	sudo apt-get install -y adduser libfontconfig
	sudo dpkg -i grafana_4.2.0_amd64.deb

- Khởi động Grafana chạy trên cổng mặc định 3000

		sudo service grafana-server start

### Install Telegraf
	wget http://get.influxdb.org/telegraf/telegraf_0.10.2-1_amd64.deb
	dpkg -i telegraf_0.10.2-1_amd64.deb

- Cấu hình Telegraf

		telegraf -sample-config > telegraf.conf

		telegraf -sample-config -input-filter cpu:mem:swap -output-filter influxdb > telegraf.conf

		telegraf -config telegraf.conf

#### Xem thống kê trên Grafana

1.) Chọn Data Sources

2.) + Add data source

4.) Điền vào:

 a.) Name: InfluxDB

 b.) Type: InfluxDB

 c.) (HTTP Settings) Url: http://localhost:8086

 d.) (InfluxDB Settings) Database: telegraf

5.) Click “Save & Test”
