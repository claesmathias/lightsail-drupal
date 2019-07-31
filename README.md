# lightsail-drupal
Drupal on AWS Lightsail

## Edit config
Edit the following lines in `user-data.txt` 
```
EMAIL=example@mail.com
URL=yoursubdomain.duckns.org
...
```

## Create instance
Create AWS Lightsail instance via [AWS Lightsail CLI](https://docs.aws.amazon.com/cli/latest/reference/lightsail/index.html "AWS Lightsail CLI")
```
aws lightsail create-instances --instance-names "drupal-vm" --availability-zone eu-west-2a --blueprint-id centos_7_1901_01 --bundle-id nano_2_0 --user-data file://user-data.txt
```
You can find the script in `/var/lib/cloud/instance/user-data.txt` on the instance

## Configure instance
### Open ports
```
aws lightsail open-instance-public-ports --port-info fromPort=443,toPort=443,protocol=TCP --instance-name drupal-vm
aws lightsail open-instance-public-ports --port-info fromPort=32400,toPort=32400,protocol=TCP --instance-name drupal-vm
```
