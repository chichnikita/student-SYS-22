# `Домашнее задание к занятию "ELK"` - `Чичулин Никита SYS-22`



<<<<<<< HEAD
1. [Описание домашнего задания к занятию «ELK»](https://github.com/netology-code/sdb-homeworks/blob/main/11-03.md#домашнее-зада)

---

### [Задание 1. Elasticsearch](https://github.com/netology-code/sdb-homeworks/blob/main/11-03.md#задание-1-elasticsearch)

Установите и запустите Elasticsearch, после чего поменяйте параметр cluster_name на случайный.

*Приведите скриншот команды 'curl -X GET 'localhost:9200/_cluster/health?pretty', сделанной на сервере с установленным Elasticsearch. Где будет виден нестандартный cluster_name*.


### Ответ 1
<details>
  <summary>Ответ 1</summary>
    1) Установить Docker и Docker Compose
    	sudo apt-get update
		sudo apt-get install docker.io docker-compose -y
    2) создать файл docker-compose.yml
    	Внести в него следующее: 
version: '3'
services:
  elasticsearch:
    image: docker.elastic.co/elasticsearch/elasticsearch:7.10.0
    environment:
      - cluster.name=my-cluster-name # Поменяйте на ваш случайный cluster_name
      - discovery.type=single-node
    ports:
      - "9200:9200"
    networks:
      - elk-network
  kibana:
    image: docker.elastic.co/kibana/kibana:7.10.0
    ports:
      - "5601:5601"
    networks:
      - elk-network
networks:
  elk-network:
    driver: bridge
    3)Поднять docker-compose
    	docker-compose up -d
    <img src = "img/ELK/1_3.png" width = 100%>
</details>







--------

### [Задание 2. Kibana](https://github.com/netology-code/sdb-homeworks/blob/main/11-03.md#задание-2-kibana)
=======
1. [Описание домашнего задания к занятию «ELKх»](https://github.com/netology-code/sdb-homeworks/blob/main/11-03.md)

---
## Дополнительные ресурсы

При выполнении задания используйте дополнительные ресурсы:
- [docker-compose elasticsearch + kibana](11-03/docker-compose.yaml);
- [поднимаем elk в docker](https://www.elastic.co/guide/en/elasticsearch/reference/7.17/docker.html);
- [поднимаем elk в docker с filebeat и docker-логами](https://www.sarulabs.com/post/5/2019-08-12/sending-docker-logs-to-elasticsearch-and-kibana-with-filebeat.html);
- [конфигурируем logstash](https://www.elastic.co/guide/en/logstash/7.17/configuration.html);
- [плагины filter для logstash](https://www.elastic.co/guide/en/logstash/current/filter-plugins.html);
- [конфигурируем filebeat](https://www.elastic.co/guide/en/beats/libbeat/5.3/config-file-format.html);
- [привязываем индексы из elastic в kibana](https://www.elastic.co/guide/en/kibana/7.17/index-patterns.html);
- [как просматривать логи в kibana](https://www.elastic.co/guide/en/kibana/current/discover.html);
- [решение ошибки increase vm.max_map_count elasticsearch](https://stackoverflow.com/questions/42889241/how-to-increase-vm-max-map-count).
---

 ### Задание 1: 
<details>
   <summary> Задание 1: Elasticsearch  </summary>
  
Установите и запустите Elasticsearch, после чего поменяйте параметр cluster_name на случайный. 

*Приведите скриншот команды 'curl -X GET 'localhost:9200/_cluster/health?pretty', сделанной на сервере с установленным Elasticsearch. Где будет виден нестандартный cluster_name*.
</details>

### Ответ 1
<details>
  <summary>Ответ 1: </summary>

![Скриншот-1](https://github.com/chichnikita/student-SYS-22/blob/main/img/11.03_1.png)
</details>


--------

 ### Задание 2: 
<details>
   <summary> Задание 2: Kibana. </summary>
>>>>>>> 00638644ef22a3be038ed287d004f9b7bd8561a9

Установите и запустите Kibana.

*Приведите скриншот интерфейса Kibana на странице http://<ip вашего сервера>:5601/app/dev_tools#/console, где будет выполнен запрос GET /_cluster/health?pretty*.

<<<<<<< HEAD
### Ответ 2
<details>
  <summary>Ответ 2</summary>
  <img src = "img/Redis-memcached caching/1_1.png" width = 100%>
</details>

--------

### [Задание 3. Logstash](https://github.com/netology-code/sdb-homeworks/blob/main/11-03.md#задание-3-logstash)

Установите и запустите Logstash и Nginx. С помощью Logstash отправьте access-лог Nginx в Elasticsearch.

*Приведите скриншот интерфейса Kibana, на котором видны логи Nginx.*

### Ответ 3
<details>
  <summary>Ответ 3</summary>
    - Запустите memcached с указанием непривилегированного пользователя:
   <img src = "img/Redis-memcached caching/2_1.png" width = 100%>
    - Установливаем ключи с TTL в 5 секунд:
   <img src = "img/Redis-memcached caching/2_2.png" width = 100%>
    - Проверяем, что ключи были удалены:
   <img src = "img/Redis-memcached caching/2_3.png" width = 100%>
    </details>


=======
</details>

 ### Ответ 2: 
<details>
   <summary> Ответ 2: </summary>

![Скриншот-2](https://github.com/chichnikita/student-SYS-22/blob/main/img/11.03_2.png)

</details>


--------


 ### Задание 3: 
<details>
   <summary> Задание 3: Logstash </summary>
  
Установите и запустите Logstash и Nginx. С помощью Logstash отправьте access-лог Nginx в Elasticsearch. 

*Приведите скриншот интерфейса Kibana, на котором видны логи Nginx.*



</details>

 ### Ответ 3: 
<details>
   <summary> Ответ 3: </summary>

![Скриншот-3](https://github.com/chichnikita/student-SYS-22/blob/main/img/11.03_3.png)

</details>
>>>>>>> 00638644ef22a3be038ed287d004f9b7bd8561a9


--------

<<<<<<< HEAD
### [Задание 4. Filebeat.](https://github.com/netology-code/sdb-homeworks/blob/main/11-03.md#задание-4-filebeat)

Установите и запустите Filebeat. Переключите поставку логов Nginx с Logstash на Filebeat.
=======

--------


 ### Задание 4: 
<details>
   <summary> Задание 4:Filebeat </summary>
  
Установите и запустите Filebeat. Переключите поставку логов Nginx с Logstash на Filebeat. 
>>>>>>> 00638644ef22a3be038ed287d004f9b7bd8561a9

*Приведите скриншот интерфейса Kibana, на котором видны логи Nginx, которые были отправлены через Filebeat.*


<<<<<<< HEAD
### Ответ 4
<details>
  <summary>Ответ 4</summary>
   1)Установить Redis 
      	sudo apt install redis-server
   2)Запись данных в Redis:
<img src = "img/Redis-memcached caching/3_1.png" width = 100%>
3)Достаём все записанные ключи и значения:
<img src = "img/Redis-memcached caching/3_2.png" width = 100%>
</details>




--------





=======

</details>

 ### Ответ 4: 
<details>
   <summary> Ответ 4: </summary>

![Скриншот-4](https://github.com/chichnikita/student-SYS-22/blob/main/img/11.03_4.png)

</details>

----
>>>>>>> 00638644ef22a3be038ed287d004f9b7bd8561a9
