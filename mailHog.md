```bash
set -x

sudo apt-get install golang-go -y
go get github.com/mailhog/MailHog
go get github.com/mailhog/mhsendmail
sudo cp go/bin/MailHog /usr/local/bin/mailhog
sudo cp go/bin/mhsendmail /usr/local/bin/mhsendmail

for php in $(ls /etc/php)
do
sudo tee /etc/php/$php/apache2/php.ini <<EOL
sendmail_path = /usr/local/bin/mhsendmail
EOL
done
read -p "Enter username" username

sudo tee /etc/systemd/system/mailhog.service <<EOL
[Unit]
Description=MailHog
After=network.target
[Service]
User=$username
ExecStart=/usr/bin/env /usr/local/bin/mailhog > /dev/null 2>&1 &
[Install]
WantedBy=multi-user.target
EOL

sudo systemctl start mailhog
sudo systemctl enable mailhog
sudo systemctl status mailhog

```