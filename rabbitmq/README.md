# rabbitmq

- bitnami rabbitmq chart

## 参考命令行安装

```
helm repo add bitnami https://charts.bitnami.com/bitnami
helm install my-release bitnami/rabbitmq
```

## 连接 rabbitmq

Credentials:

    echo "Username      : user"
    echo "Password      : $(kubectl get secret --namespace data rabbitmq -o jsonpath="{.data.rabbitmq-password}" | base64 --decode)"
    echo "ErLang Cookie : $(kubectl get secret --namespace data rabbitmq -o jsonpath="{.data.rabbitmq-erlang-cookie}" | base64 --decode)"

RabbitMQ can be accessed within the cluster on port at rabbitmq.data.svc.

To access for outside the cluster, perform the following steps:

To Access the RabbitMQ AMQP port:

    echo "URL : amqp://127.0.0.1:5672/"
    kubectl port-forward --namespace data svc/rabbitmq 5672:5672

To Access the RabbitMQ Management interface:

    echo "URL : http://127.0.0.1:15672/"
    kubectl port-forward --namespace data svc/rabbitmq 15672:15672
