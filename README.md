# Stafi-node-check

very 5 minutes the script checks the system's basic parameters. If memory, storage or CPU load exceeds 80%, the script sends a warning e-mail. Simple. It also sends notifications when the number of peers drops to 20, blocks lag exceeds 60 and a new version of the node appears.

Installation
git clone https://github.com/nikolayqwerty/stafi-node-monitor.git
cd stafi-node-monitor
sudo apt install python3-pip
pip3 install -r requirements.txt
Edit conf file:

nano conf.ini
Change these lines to your email and password from the yandex mail and emails for notifications.

yandex_login = your-mail@yandex.ru
yandex_password = your-password
to_mail = mail1@gmail.com mail2@gmail.com
For the validator node with sentry need to specify the number of sentry nodes. For example, 1. For sentry nodes or validator without sentry, leave the value 0.

sentry_nodes_count = 0
Add the task to the crontab

crontab -e
SHELL=/bin/bash
*/5 * * * * cd ~/stafi-node-monitor/ && python3 ~/stafi-node-monitor/main.py > /dev/null 2>&1
