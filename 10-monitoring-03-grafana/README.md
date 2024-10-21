# Домашнее задание к занятию 14 «Средство визуализации Grafana»

## Задание повышенной сложности

**При решении задания 1** не используйте директорию [help](./help) для сборки проекта. Самостоятельно разверните grafana, где в роли источника данных будет выступать prometheus, а сборщиком данных будет node-exporter:

- grafana;
- prometheus-server;
- prometheus node-exporter.

За дополнительными материалами можете обратиться в официальную документацию grafana и prometheus.

В решении к домашнему заданию также приведите все конфигурации, скрипты, манифесты, которые вы 
использовали в процессе решения задания.

**При решении задания 3** вы должны самостоятельно завести удобный для вас канал нотификации, например, Telegram или email, и отправить туда тестовые события.

В решении приведите скриншоты тестовых событий из каналов нотификаций.

## Обязательные задания

### Задание 1

1. Используя директорию [help](./help) внутри этого домашнего задания, запустите связку prometheus-grafana.
1. Зайдите в веб-интерфейс grafana, используя авторизационные данные, указанные в манифесте docker-compose.
1. Подключите поднятый вами prometheus, как источник данных.
1. Решение домашнего задания — скриншот веб-интерфейса grafana со списком подключенных Datasource.

### Ответ 1


<img width="1421" alt="Снимок экрана 2024-10-21 в 14 54 20" src="https://github.com/user-attachments/assets/7d3f1633-f740-4c28-96e7-a287f9e1e5f5">

<img width="1291" alt="Снимок экрана 2024-10-21 в 14 46 58" src="https://github.com/user-attachments/assets/bccf19a8-9618-4c8a-a04e-00d0c417e9a2">

<img width="1256" alt="Снимок экрана 2024-10-21 в 14 54 57" src="https://github.com/user-attachments/assets/d4c0924e-29cd-4577-b574-3e3c09be9d71">




## Задание 2

Изучите самостоятельно ресурсы:

1. [PromQL tutorial for beginners and humans](https://valyala.medium.com/promql-tutorial-for-beginners-9ab455142085).
1. [Understanding Machine CPU usage](https://www.robustperception.io/understanding-machine-cpu-usage).
1. [Introduction to PromQL, the Prometheus query language](https://grafana.com/blog/2020/02/04/introduction-to-promql-the-prometheus-query-language/).

Создайте Dashboard и в ней создайте Panels:

- утилизация CPU для nodeexporter (в процентах, 100-idle);
- CPULA 1/5/15;
- количество свободной оперативной памяти;
- количество места на файловой системе.

Для решения этого задания приведите promql-запросы для выдачи этих метрик, а также скриншот получившейся Dashboard.

### Ответ 2


- утилизация CPU для nodeexporter (в процентах, 100-idle);
  ```
  avg without (cpu)(irate(node_cpu_seconds_total{job="nodeexporter",mode="idle"}[1m]))
  ```
- CPULA 1/5/15;
  ```
  node_load1{job="nodeexporter"}
  node_load5{job="nodeexporter"}
  node_load15{job="nodeexporter"}
  ```
- количество свободной оперативной памяти;
  ```
  node_memory_MemFree_bytes{job='nodeexporter'}
  ```
- количество места на файловой системе.
  ```
  node_filesystem_avail_bytes{instance="nodeexporter:9100", job="nodeexporter", mountpoint="/"}
  ```

<img width="1421" alt="Снимок экрана 2024-10-21 в 15 39 35" src="https://github.com/user-attachments/assets/cae74d62-151f-4bd8-b152-9730e213b7ce">


## Задание 3

1. Создайте для каждой Dashboard подходящее правило alert — можно обратиться к первой лекции в блоке «Мониторинг».
1. В качестве решения задания приведите скриншот вашей итоговой Dashboard.

   

### Ответ 3 


<img width="985" alt="Снимок экрана 2024-10-21 в 16 54 12" src="https://github.com/user-attachments/assets/34672537-b776-488d-ab95-76975fc508ce">

<img width="1020" alt="Снимок экрана 2024-10-21 в 16 54 18" src="https://github.com/user-attachments/assets/644c75f9-e6bb-439f-828a-0fabb9195f89">


## Задание 4

1. Сохраните ваш Dashboard.Для этого перейдите в настройки Dashboard, выберите в боковом меню «JSON MODEL». Далее скопируйте отображаемое json-содержимое в отдельный файл и сохраните его.
1. В качестве решения задания приведите листинг этого файла.

### Ответ 4 

[dashboard.json](https://github.com/alexandreevich/mnt-homeworks/blob/MNT-video/10-monitoring-03-grafana/dashboard.json)

---

### Как оформить решение задания

Выполненное домашнее задание пришлите в виде ссылки на .md-файл в вашем репозитории.

---
