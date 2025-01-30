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

2. `Заполните здесь этапы выполнения, если требуется ....`
3. `Заполните здесь этапы выполнения, если требуется ....`
4. `Заполните здесь этапы выполнения, если требуется ....`
5. `Заполните здесь этапы выполнения, если требуется ....`
6. 

```
Поле для вставки кода...
....
....
....
....
```

`При необходимости прикрепитe сюда скриншоты
![Название скриншота](ссылка на скриншот)`


















### Задание 4

`Приведите ответ в свободной форме........`

1. `Заполните здесь этапы выполнения, если требуется ....`
2. `Заполните здесь этапы выполнения, если требуется ....`
3. `Заполните здесь этапы выполнения, если требуется ....`
4. `Заполните здесь этапы выполнения, если требуется ....`
5. `Заполните здесь этапы выполнения, если требуется ....`
6. 

```
Поле для вставки кода...
....
....
....
....
```

`При необходимости прикрепитe сюда скриншоты
![Название скриншота](ссылка на скриншот)`
