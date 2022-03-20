## Reboot instance with CLI

`aws ec2 reboot-instances --instance-ids i-1234567890abcdef5`

## Install Apache Http server (Linux)

```
sudo apt-get update -y
sudo apt-get install apache2 -y
sudo groupadd www
sudo usermod -a -G www ubuntu
sudo chown -R root:www /var/www
```

