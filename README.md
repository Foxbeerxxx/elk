# Домашнее задание к занятию "`ELK`" - `Татаринцев Алексей`




### Задание 1 Elasticsearch


1. `Работаю без докера, подготавливаю установку на хостовую машину Elasticsearch`

```
sudo apt update
sudo apt install -y apt-transport-https
wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
echo "deb https://artifacts.elastic.co/packages/8.x/apt stable main" | sudo tee -a /etc/apt/sources.list.d/elastic-8.x.list
sudo apt update

```
2. `Установка Elasticsearch`
```
sudo apt install -y elasticsearch

```
3. `Проверяю установленный сервис`

![1](https://github.com/Foxbeerxxx/elk/blob/main/img/img1.png)`


4. `Меняю конфигурацию файла`
```
sudo nano /etc/elasticsearch/elasticsearch.yml

```
![2](https://github.com/Foxbeerxxx/elk/blob/main/img/img2.png)`

5. `Перезагружаем сервис`

```
sudo systemctl restart elasticsearch

```
6. `И пробуем обращаться через curl на локал хост по порту 9200`

```
 curl -X GET 'localhost:9200/_cluster/health?pretty'    

```
![3](https://github.com/Foxbeerxxx/elk/blob/main/img/img3.png)`

---

### Задание 2 Kibana

1. `Устанавливаю Kibana`
![4](https://github.com/Foxbeerxxx/elk/blob/main/img/img4.png)`


2. `Редактирую конф файл `
```
  sudo nano /etc/kibana/kibana.yml
```  
![5](https://github.com/Foxbeerxxx/elk/blob/main/img/img5.png)`

3. `Запускаю и проверяю статус`
![6](https://github.com/Foxbeerxxx/elk/blob/main/img/img6.png)`

4. `Захожу http://localhost:5601/ `

![7](https://github.com/Foxbeerxxx/elk/blob/main/img/img7.png)`


5. `Захожу в devtools и выполняю код`
``` 
 GET /_cluster/health?pretty

``` 
![8](https://github.com/Foxbeerxxx/elk/blob/main/img/img8.png)`

---

### Задание 3 Logstash

1. `Устанавливаю сервис и проверяю, что он запустился`
```
sudo apt install logstash
```
![9](https://github.com/Foxbeerxxx/elk/blob/main/img/img9.png)`

2. `В общем попытался настроить метрику, ругается ничего не понятно`
![10](https://github.com/Foxbeerxxx/elk/blob/main/img/img10.png)`

3. `После продолжительного ТЫКания, добаляю метрику`
![12](https://github.com/Foxbeerxxx/elk/blob/main/img/img12.png)`

4. `Discover высвечивается нужная метрика, но как в лекции по времени классифицивароть то зависает выбрасывает`
![13](https://github.com/Foxbeerxxx/elk/blob/main/img/img13.png)`

### Задание 4 Filebeat

1. `Устанавливаю filebeat и проверяю`
```
sudo apt install filebeat
```

2. `После установки все сломалось :^) `
![11](https://github.com/Foxbeerxxx/elk/blob/main/img/img11.png)`

`Пробую перезагрузить сервис sudo systemctl restart elasticsearch
, не поммогает, перезагружаю хост целиком `
`Ничего не помогло`
3. `Редкатирую конф файл `
```
sudo nano /etc/filebeat/filebeat.yml
```
3.1. `Проверяю статус`
```
  sudo systemctl start filebeat
```
![14](https://github.com/Foxbeerxxx/elk/blob/main/img/img14.png)`


4. `Описываю здесь работу по лекции , так как сервис лег целиком, видимо из за моего старенького Sony`

`Основные изменения в конфигурации:`
` filebeat.inputs: Настройте вход для логов Nginx. Укажите пути к файлам логов. Обычно это /var/log/nginx/access.log и /var/log/nginx/error.log`

```
   filebeat.inputs:
     - type: log
       enabled: true
       paths:
         - /var/log/nginx/access.log
         - /var/log/nginx/error.log
       tags: ["nginx"]
     
     setup.kibana:
      host: "http://localhost:5601"  
```