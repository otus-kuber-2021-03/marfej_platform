# Выполнено ДЗ №1

В процессе сделано:

   - Настроено локальное окружение.
   - Написан Dockerfile и собран контейнер с веб серевером nginx. Контейнер помещен в docker hub.
   - Собран контейнер с фронтендом Hipster Shop. Контейнер помещен в docker hub.

## Задание 1
Разберитесь почему все pod в namespace kube-system восстановились
после удаления.

Ответ: Поды кроме coredns являются статическими и управляются непосредственно kubelet. Для coredns указано количество реплик - 1, поэтому он запускается после старта статических подов.

## Задание со звездочкой
Выясните причину, по которой pod frontend находится в статусе Error.

Ответ: Для работы сервиса необходимы переменные окружения.

# Выполнено ДЗ №2

Выполнено:

   - Созданы ReplicaSet для frontend и paymentservice.
   - Создан Deployment для paymentservice.
   - Проверены стратегии Blue-green и Reverse rolling update для Deployment (⭐).
   - Настроен Readiness Probe для сервиса frontend.
   - Настроен DaemonSet для Node Exporter (⭐, ⭐⭐). 

Почему обновление ReplicaSet не повлекло обновление
запущенных pod?

Ответ:  ReplicaSet не умеет обновлять в частности шаблоны контейнеров. 

# Выполнено ДЗ №3

Выполнено:

    - Создатs Service Account
    - Назначены права

# Выполнено ДЗ №4
    - Развернут StatefulSet
    - Данные перенесены в Secret (*)

# Выполнено ДЗ №5

Выполнено:

    - Добавлены проверки (ReadinessProbe, LivenessProbe)
    - Создан объект Deployment
    - Добавлен сервис в кластер (ClusterIP)
    - Включен режим балансировки IPVS
    - Установлен MetaILB
    - Добавлен сервис LoadBalancer
    - Установлен ingress-nginx
    - Cозданы правила Ingress
    - Установлен kubernetes-dashboard и настроен префикс (*)

# Выполнено ДЗ №7

Выполнено:

    - Cозданы Custom Resource и Custom Resource Definition
    - Создан оператор. Образ загружен в dockerhub
    - Произведен deploy оператора

Вывод kubectl get jobs:
NAME                         COMPLETIONS   DURATION   AGE
backup-mysql-instance-job    1/1           6s         16m
restore-mysql-instance-job   1/1           25m        25m

Вывод kubectl exec -it $MYSQLPOD -- mysql -potuspassword -e "select * from test;" otus-database:
mysql: [Warning] Using a password on the command line interface can be insecure.
+----+-------------+
| id | name        |
+----+-------------+
|  1 | some data   |
|  2 | some data-2 |
+----+-------------+

# Выполнено ДЗ kubernetes-storage

Выполнено:

    - Установлен драйвер [CSI Host Path Driver](https://github.com/kubernetes-csi/csi-driver-host-path)
    - Создан StorageClass
    - Создан PVC
    - Создан Pod
    - Проверо создание и восстановление снапшотов

 
# Выполнено ДЗ kubernetes-debug

Выполнено:

    - Усноновлен kubectl-debug
    - Проверена работа kubectl-debug с агентом и с DaemonSet
    - Запущено тестовое приложение, проверена работа политик сети
    - Настроен сбор и отображение логов сетевых политик



 