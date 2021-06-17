# mysql

- bitnami mysql chart
- bitnami phpmyadmin chart

## 参考命令行安装

```
helm repo add bitnami https://charts.bitnami.com/bitnami
helm install my-release bitnami/mysql
```

## 连接 mysql

Tip:

Watch the deployment status using the command: kubectl get pods -w --namespace data

Services:

echo Primary: mysql.data.svc.cluster.local:3306

Administrator credentials:

echo Username: root
echo Password : $(kubectl get secret --namespace data mysql -o jsonpath="{.data.mysql-root-password}" | base64 --decode)

To connect to your database:

1. Run a pod that you can use as a client:

   kubectl run mysql-client --rm --tty -i --restart='Never' --image docker.io/bitnami/mysql:8.0.23-debian-10-r57 --namespace data --command -- bash

2. To connect to primary service (read/write):

   mysql -h mysql.data.svc.cluster.local -uroot -p my_database

To upgrade this helm chart:

1. Obtain the password as described on the 'Administrator credentials' section and set the 'root.password' parameter as shown below:

   ROOT_PASSWORD=$(kubectl get secret --namespace data mysql -o jsonpath="{.data.mysql-root-password}" | base64 --decode)
      helm upgrade mysql bitnami/mysql --set auth.rootPassword=$ROOT_PASSWORD

## phpmyadmin
