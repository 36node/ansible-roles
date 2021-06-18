# redis

安装 redis

# 其他

- bitnami redis chart

## 参考命令行安装

```
helm repo add bitnami https://charts.bitnami.com/bitnami
helm install my-release bitnami/redis
```

## 连接 redis

Redis(TM) can be accessed via port 6379 on the following DNS names from within your cluster:

redis-master.data.svc.cluster.local for read/write operations
redis-slave.data.svc.cluster.local for read-only operations

To get your password run:

    export REDIS_PASSWORD=$(kubectl get secret --namespace data redis -o jsonpath="{.data.redis-password}" | base64 --decode)

To connect to your Redis(TM) server:

1. Run a Redis(TM) pod that you can use as a client:
   kubectl run --namespace data redis-client --rm --tty -i --restart='Never' \
    --env REDIS_PASSWORD=$REDIS_PASSWORD \
   --image docker.io/bitnami/redis:6.0.12-debian-10-r3 -- bash

2. Connect using the Redis(TM) CLI:
   redis-cli -h redis-master -a $REDIS_PASSWORD
   redis-cli -h redis-slave -a $REDIS_PASSWORD

To connect to your database from outside the cluster execute the following commands:

    kubectl port-forward --namespace data svc/redis-master 6379:6379 &
    redis-cli -h 127.0.0.1 -p 6379 -a $REDIS_PASSWORD
