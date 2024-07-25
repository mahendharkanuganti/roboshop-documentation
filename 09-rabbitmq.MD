### RabbitMQ

RabbitMQ is a messaging Queue which is used by some components of the applications.

Configure YUM Repos from the script provided by vendor.

```
curl -s https://packagecloud.io/install/repositories/rabbitmq/erlang/script.rpm.sh | bash
```

Configure YUM Repos for RabbitMQ.

```
curl -s https://packagecloud.io/install/repositories/rabbitmq/rabbitmq-server/script.rpm.sh | bash
```

Install RabbitMQ

```
dnf install rabbitmq-server -y 
```

Start RabbitMQ Service

```
systemctl enable rabbitmq-server 
```

```
systemctl start rabbitmq-server 
```

RabbitMQ comes with a default username / password as guest/guest. But this user cannot be used to connect. Hence, we need to create one user for the application.

```
rabbitmqctl add_user roboshop roboshop123
```
```
rabbitmqctl set_permissions -p / roboshop ".*" ".*" ".*"
```
* validate if the port 25672 is opened or not for internet facing IP (0 0.0.0.0:25672)
```
netstat -lntp
```
* Then add the 25672 port in EC2 security group inbound rules.
* Also verify the port 4369 if its causing any connectivity issue
