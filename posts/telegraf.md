sudo subl /usr/local/etc/telegraf.conf 
brew services restart telegraf
tail -f /usr/local/var/log/telegraf.log