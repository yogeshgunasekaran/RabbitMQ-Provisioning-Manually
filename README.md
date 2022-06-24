# RabbitMQ-Provisioning-Manually
Installation of RabbitMQ in CentOS7
### Login to the root user
```sh
sudo su -
```
### Update OS with latest patches
 ```sh 
 yum update -y 
 ```
### Set EPLEL Repository
 ```sh
  yum install epel-release -y 
 ```
### Install Dependencies
```sh
 yum install wget -y
 ```
```sh
 cd /tmp/
 ```
 ```sh
 wget http://packages.erlang-solutions.com/erlang-solutions-2.0-1.noarch.rpm 
 ```
 ```sh
 rpm -Uvh erlang-solutions-2.0-1.noarch.rpm
 ```
 ```sh
 yum -y install erlang socat
 ```
 ### Install Rabbitmq Server
 ```sh
 curl -s https://packagecloud.io/install/repositories/rabbitmq/rabbitmq-server/script.rpm.sh | sudo bash
 ```
 ```sh
 yum install rabbitmq-server -y
 ```
 ### Start & Enable RabbitMQ
 ```sh
 systemctl start rabbitmq-server
 ```
 ```sh
 systemctl enable rabbitmq-server
 ```
  ```sh
 systemctl status rabbitmq-server
 ```
 ### Config Change
 ```sh
 sh -c 'echo "[{rabbit, [{loopback_users, []}]}]." > /etc/rabbitmq/rabbitmq.config'
 ```
 ```sh
 rabbitmqctl add_user test test
 ```
  ```sh
 rabbitmqctl set_user_tags test administrator
 ```
 ### Restart RabbitMQ service
 ```sh
 systemctl restart rabbitmq-server
 ```
 ### Enabling the firewall and allowing port 25672 to access the rabbitmq permanently (Optional)
 ```sh
 systemctl start firewalld
 ```
 ```sh
 systemctl enable firewalld
 ```
 ```sh
 firewall-cmd --get-active-zones
 ```
 ```sh
 firewall-cmd --zone=public --add-port=25672/tcp --permanent
 ```
 ```sh
 firewall-cmd --reload
 ```
 
 
 
