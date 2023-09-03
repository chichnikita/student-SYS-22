# `Домашнее задание к занятию "Disaster recovery и Keepalived"` - `Чичулин Никита SYS-22`



1. [Описание домашнего задания к занятию «Disaster recovery и Keepalived»](https://github.com/netology-code/sflt-homeworks/blob/main/1.md)

---

1. ### Задание 1

   - Дана [схема](https://github.com/netology-code/sflt-homeworks/blob/main/1/hsrp_advanced.pkt) для Cisco Packet Tracer, рассматриваемая в лекции.
   - На данной схеме уже настроено отслеживание интерфейсов маршрутизаторов Gi0/1 (для нулевой группы)
   - Необходимо аналогично настроить отслеживание состояния интерфейсов Gi0/0 (для первой группы).
   - Для проверки корректности настройки, разорвите один из кабелей между одним из маршрутизаторов и Switch0 и запустите ping между PC0 и Server0.
   - На проверку отправьте получившуюся схему в формате pkt и скриншот, где виден процесс настройки маршрутизатора.



### Ответ 1

<img src = "img/Disaster recovery и Keepalived/1_1.png" width = 100%>

<img src = "img/Disaster recovery и Keepalived/1_2.png" width = 100%>

<img src = "img/Disaster recovery и Keepalived/1_3.png" width = 100%>

[Файл .pkt](https://github.com/chichnikita/student-SYS-22/tree/main/img/files/hsrp_advanced_DZ1.pkt)

--------

1. ### Задание 2

   - Запустите две виртуальные машины Linux, установите и настройте сервис Keepalived как в лекции, используя пример конфигурационного [файла](https://github.com/Ivashka80/Disaster-recovery_Keepalived/blob/main/1/keepalived-simple.conf).
   - Настройте любой веб-сервер (например, nginx или simple python server) на двух виртуальных машинах
   - Напишите Bash-скрипт, который будет проверять доступность порта данного веб-сервера и существование файла index.html в root-директории данного веб-сервера.
   - Настройте Keepalived так, чтобы он запускал данный скрипт каждые 3 секунды и переносил виртуальный IP на другой сервер, если bash-скрипт завершался с кодом, отличным от нуля (то есть порт веб-сервера был недоступен или отсутствовал index.html). Используйте для этого секцию vrrp_script
   - На проверку отправьте получившейся bash-скрипт и конфигурационный файл keepalived, а также скриншот с демонстрацией переезда плавающего ip на другой сервер в случае недоступности порта или файла index.html

### Ответ 2

```bash
#!/bin/bash
if [[ $(netstat -tuln | grep LISTEN | grep :80) ]] && [[ -f /var/www/html/index.nginx-debian.html ]]; then
        exit 0
else
        sudo systemctl stop keepalived
fi
```

keepalived.conf :

```bash
vrrp_script check_script {
      script "/home/chistov/check_nginx.sh"
      interval 3
}

vrrp_instance VI_1 {
        state MASTER
        interface enp0s3
        virtual_router_id 25
        priority 255
        advert_int 1

        virtual_ipaddress {
              192.168.255.225/24
        }

        track_script {
                   check_script
                }
}
```

<img src = "img/Disaster recovery и Keepalived/2_1.png" width = 100%>

<img src = "img/Disaster recovery и Keepalived/2_2.png" width = 100%>

<img src = "img/Disaster recovery и Keepalived/2_3.png" width = 100%>

<img src = "img/Disaster recovery и Keepalived/2_4.png" width = 100%>