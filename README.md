Dockerized Zabbix Server 5.0 Installation Script
This script, installs and configures a dockerized zabbix 5.0 server in a fully automated way on CentOS 7 platforms.

Here's the summary:

Enables Epel repo.
Installs docker (ce), docker compose and jq.
Creates self signed SSL certificates for zabbix and grafana frontends.
Deploys zabbix services via docker compose.
Invokes the zabbix API to do following configurations.
Creates a bunch of hosts group.
Creates auto registration actions for Linux and Windows hosts.
Tune Linux / Windows Templates items:
Set FS discovery interval 30m for linux template
Set network interface discovery interval 30m for linux template
Set total memory check interval 5m for linux template
Set total swap check interval 30m for linux template
Set Number of CPUs interval 30m for linux template.
Set FS discovery interval 30m for Windows template
Set network interface discovery interval 30m for Windows template
Add free memory usege as percent for Windows
Disable annoying service discovery rules which creates too mant false positive alerts.
Adds alexanderzobnin-zabbix-app datasource plugin to grafana.
Adds briangann-gauge-panel, btplc-trend-box-panel and jdbranham-diagram-panel plugins to grafana.
Invokes the grafana API to add custom Linux / Windows dashboards as well as Zabbix overall system status dashboard.
Sets email notification for admin user. (Optional)
Sets slack notification for admin user. (Optional)
Changes the default notification messages in a more informative manner.
Usage
To invoke zabbix server installation, execute the "zabbix-server" script with "init" parameter and follow the instructions.

# bash scripts/zabbix-server.sh init
You can find an complete example output at the end of the page.

Accessing Zabbix and Grafana UIs
Zabbix ui is accessible on port 8443 with the credentials listed below:

URL: https://host-ip:8443
Username: Admin
Password: zabbix
and grafana is on port 3000:

URL: https://host-ip:3000
Username: admin
Password: zabbix
Note: Both services are served over https by using a self-signed certificate.
