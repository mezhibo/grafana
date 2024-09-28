
**Задание 1**

1. Используя директорию help внутри этого домашнего задания, запустите связку prometheus-grafana.

2. Зайдите в веб-интерфейс grafana, используя авторизационные данные, указанные в манифесте docker-compose.

3. Подключите поднятый вами prometheus, как источник данных.

4. Решение домашнего задания — скриншот веб-интерфейса grafana со списком подключенных Datasource.


**Решение 1**

Запустили Графану и добаваили источник данных наш прометеус 

![alt text](https://github.com/mezhibo/grafana/blob/9d4d7e0677ee6afacee720fd61013cf0850dd9ab/IMG/1.jpg)


![alt text](https://github.com/mezhibo/grafana/blob/9d4d7e0677ee6afacee720fd61013cf0850dd9ab/IMG/2.jpg)

**Задание 2**

Изучите самостоятельно ресурсы:

1. PromQL tutorial for beginners and humans.

2. Understanding Machine CPU usage.

3.Introduction to PromQL, the Prometheus query language.


Создайте Dashboard и в ней создайте Panels:

 - утилизация CPU для nodeexporter (в процентах, 100-idle);

 - CPULA 1/5/15;

 - количество свободной оперативной памяти;

 - количество места на файловой системе.

Для решения этого задания приведите promql-запросы для выдачи этих метрик, а также скриншот получившейся Dashboard.


**Решение 2**

1. утилизация CPU для nodeexporter (в процентах, 100-idle);

100 - avg(irate(node_cpu_seconds_total{mode="idle"}[5m])) * 100

![alt text](https://github.com/mezhibo/grafana/blob/9d4d7e0677ee6afacee720fd61013cf0850dd9ab/IMG/3.jpg)


2. CPULA 1/5/15;

avg by (instance)(rate(node_load1{}[1m])) avg by (instance)(rate(node_load5{}[1m])) avg by (instance)(rate(node_load15{}[1m]))


![alt text](https://github.com/mezhibo/grafana/blob/9d4d7e0677ee6afacee720fd61013cf0850dd9ab/IMG/4.jpg)




3. количество свободной оперативной памяти;
   
node_memory_MemFree_bytes{instance="nodeexporter:9100",job="nodeexporter"}

![alt text](https://github.com/mezhibo/grafana/blob/9d4d7e0677ee6afacee720fd61013cf0850dd9ab/IMG/5.jpg)


4. количество места на файловой системе.
   
node_filesystem_avail_bytes{mountpoint="/"}

![alt text](https://github.com/mezhibo/grafana/blob/9d4d7e0677ee6afacee720fd61013cf0850dd9ab/IMG/6.jpg)


Весь дашборд

![alt text](https://github.com/mezhibo/grafana/blob/9d4d7e0677ee6afacee720fd61013cf0850dd9ab/IMG/7.jpg)


**Задание 3**

1. Создайте для каждой Dashboard подходящее правило alert — можно обратиться к первой лекции в блоке «Мониторинг».

2. В качестве решения задания приведите скриншот вашей итоговой Dashboard.


**Решение 3**

Выстраиваем все ползунки алертинга аналогично этому

![alt text](https://github.com/mezhibo/grafana/blob/312234525272360c8828ab5d12df6a07d8929fff/IMG/9.jpg)



![alt text](https://github.com/mezhibo/grafana/blob/312234525272360c8828ab5d12df6a07d8929fff/IMG/8.jpg)

**Задание 4**

1.Сохраните ваш Dashboard.Для этого перейдите в настройки Dashboard, выберите в боковом меню «JSON MODEL». Далее скопируйте отображаемое json-содержимое в отдельный файл и сохраните его.

2. В качестве решения задания приведите листинг этого файла.


**Решение 4**

[ДАШБОРД!!!!!](https://github.com/mezhibo/grafana/blob/312234525272360c8828ab5d12df6a07d8929fff/IMG/JSON_model_Dashboard.json)
