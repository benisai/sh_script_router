# tomato-grafana

Scripts to display metrics from routers running DD-WRT. Developed on Netgear R7000.

# Requirements

- Router running FreshTomato (tested on 2021.2)
- Server running Grafana
- Server running InfluxDB with auth-enabled=true

# Installation

Enable JFFS support on Tomato under Administration -> JFFS.

Upload all shell scripts to /jffs/dd-wrt-grafana/. Modify the IP, port, password, and username of your influxdb server in variables.sh

Add the following three commands under Administration -> Scheduler as custom cron jobs:
```
sh /jffs/dd-wrt-grafana/collector.sh >/dev/null 2>&1
sh /jffs/dd-wrt-grafana/collector20.sh >/dev/null 2>&1
sh /jffs/dd-wrt-grafana/collector40.sh >/dev/null 2>&1
```
These should all run every 1 minute on every day of the week.

Import Grafana json dashbaord.

Enjoy.
