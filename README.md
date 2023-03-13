# Домашнее задание к занятию 11.4. «Очереди RabbitMQ» Баранов Сергей

---

### Задание 1. Установка RabbitMQ

Используя Vagrant или VirtualBox, создайте виртуальную машину и установите RabbitMQ.
Добавьте management plug-in и зайдите в веб-интерфейс.

*Итогом выполнения домашнего задания будет приложенный скриншот веб-интерфейса RabbitMQ.*

![monitoring](https://github.com/12sergey12/11.04_rabbitMQ/blob/main/images/11.4-1.png)


---

### Задание 2. Отправка и получение сообщений

Используя приложенные скрипты, проведите тестовую отправку и получение сообщения.
Для отправки сообщений необходимо запустить скрипт producer.py.
Для работы скриптов вам необходимо установить Python версии 3 и библиотеку Pika.
Также в скриптах нужно указать IP-адрес машины, на которой запущен RabbitMQ, заменив localhost на нужный IP.

```shell script
$ pip install pika
```

Зайдите в веб-интерфейс, найдите очередь под названием hello и сделайте скриншот.
После чего запустите второй скрипт consumer.py и сделайте скриншот результата выполнения скрипта

*В качестве решения домашнего задания приложите оба скриншота, сделанных на этапе выполнения.*

Для закрепления материала можете попробовать модифицировать скрипты, чтобы поменять название очереди и отправляемое сообщение.

![monitoring](https://github.com/12sergey12/11.04_rabbitMQ/blob/main/images/11.4-2.png)

![monitoring](https://github.com/12sergey12/11.04_rabbitMQ/blob/main/images/11.4-22.png)

![monitoring](https://github.com/12sergey12/11.04_rabbitMQ/blob/main/images/11.04-23.png)

![monitoring](https://github.com/12sergey12/11.04_rabbitMQ/blob/main/images/11.04-28.png)


---

### Задание 3. Подготовка HA кластера

Используя Vagrant или VirtualBox, создайте вторую виртуальную машину и установите RabbitMQ.
Добавьте в файл hosts название и IP-адрес каждой машины, чтобы машины могли видеть друг друга по имени.

Пример содержимого hosts файла:
```shell script
$ cat /etc/hosts
192.168.0.10 rmq01
192.168.0.11 rmq02
```
После этого ваши машины могут пинговаться по имени.

Затем объедините две машины в кластер и создайте политику ha-all на все очереди.

*В качестве решения домашнего задания приложите скриншоты из веб-интерфейса с информацией о доступных нодах в кластере и включённой политикой.*

Также приложите вывод команды с двух нод:

```shell script
$ rabbitmqctl cluster_status
```

Для закрепления материала снова запустите скрипт producer.py и приложите скриншот выполнения команды на каждой из нод:

```shell script
$ rabbitmqadmin get queue='hello'
```

После чего попробуйте отключить одну из нод, желательно ту, к которой подключались из скрипта, затем поправьте параметры подключения в скрипте consumer.py на вторую ноду и запустите его.

*Приложите скриншот результата работы второго скрипта.*

![monitoring](https://github.com/12sergey12/11.04_rabbitMQ/blob/main/images/11.04-33.png)

![monitoring](https://github.com/12sergey12/11.04_rabbitMQ/blob/main/images/11.04-333mq1.png)

![monitoring](https://github.com/12sergey12/11.04_rabbitMQ/blob/main/images/11.04-333mq2.png)

![monitoring](https://github.com/12sergey12/11.04_rabbitMQ/blob/main/images/11.04-36.png)

![monitoring](https://github.com/12sergey12/11.04_rabbitMQ/blob/main/images/11.04-3_mq1_hello.png)

![monitoring](https://github.com/12sergey12/11.04_rabbitMQ/blob/main/images/11.04-3_mq2_hello.png)

![monitoring](https://github.com/12sergey12/11.04_rabbitMQ/blob/main/images/11.04-3_status.png)

![monitoring](https://github.com/12sergey12/11.04_rabbitMQ/blob/main/images/11.04-3_stop_app_mq2.png)



