Руководствуясь материалами лекции опишите произошедшую
ситуацию, почему обновление ReplicaSet не повлекло обновление
запущенных pod?



Задание со зведочкой
  - Blue-green
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxSurge: 3
      maxUnavailable: 0

 - Reverse Rolling Update
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxSurge: 0
      maxUnavailable: 1



$kubectl get rs
NAME                        DESIRED   CURRENT   READY   AGE
frontend                    3         3         3       92m
paymentservice-5b5fb5c4ff   0         0         0       5m4s
paymentservice-6d45447f58   3         3         3       2m21s




kubectl get rs -l app=paymentservice -w