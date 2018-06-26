# I. Моделирование взаимодействия «клиент-сервер» с помощью программы telnet и программы curl
### 1. Кодируем свои имя и фамилию в node.js, используя функцию encodeURIComponent()
![alt](https://pp.userapi.com/c844722/v844722160/893e9/Mez2whLxRd0.jpg)
### 2. Проверяем, подключен ли telnet в настройках системы
### 3. Скачиваем curl, если он не установлен
### 4. Выполняем POST-запрос с помощью curl

`curl -i  -d "name=%D0%90%D1%80%D0%B8%D0%BD%D0%B0&familyname=%D0%A1%D0%B0%D1%84%D0%B8%D1%83%D0%BB%D0%BB%D0%B8%D0%BD%D0%B0" -X POST http://kodaktor.ru/api/req/%D0%90%D1%80%D0%B8%D0%BD%D0%B0/%D0%A1%D0%B0%D1%84%D0%B8%D1%83%D0%BB%D0%BB%D0%B8%D0%BD%D0%B0`
  
Нажимаем enter и :
### 5.Результат
![alt](https://pp.userapi.com/c845417/v845417550/872d0/UP2oj3kYSD8.jpg)
где __X-Test : POSTa04ae827765b7ff47e2fb80e28f8ec10__  

# II. Создание простого веб-сервера на основе Node.js
### 1. Инициализируем проект в командной строке
![alt](https://pp.userapi.com/c845417/v845417550/87561/4hESW4ymRv0.jpg)
### 2. Устанавливаем инструмент nodemon для автоматизации перезапуска сценария и moment для работы с датой и временем  
`npm i -D nodemon`  
`npm i moment`  
### 3. Вносим изменения в package.json файл, чтобы nodemon стартовал вместе с приложением - добавляем `"scripts": {"start": "nodemon"},`  
![alt](https://pp.userapi.com/c845324/v845324413/8bd17/-UMvl2JvpuU.jpg)
### 4.Создаём файл index.js рядом с package.json, в котором будет код сервера
![alt](https://pp.userapi.com/c845324/v845324586/89d85/lPDRzY5xVJQ.jpg)
### 5.Запускаем index.js и проверяем его результат через curl : `curl localhost:4321` 
![alt](https://pp.userapi.com/c845417/v845417963/87138/5wvfdUQcT-Q.jpg)
### и в браузере 
![alt](https://pp.userapi.com/c845417/v845417963/8713f/WKrVyP9E3UU.jpg)
### 6. Добавляем к проекту поддержку выдачи данных в формате JSON с выдачей соответствующего заголовка и кодировки UTF-8
![alt](https://pp.userapi.com/c845417/v845417963/87172/S5UlKcClhOE.jpg)
### 7. Проверяем
![alt](https://pp.userapi.com/c845417/v845417963/87180/BFvDPxzvj6w.jpg)
### 8.  Рефакторинг кода : чтобы коллбэк, отвечающий на запросы, явным образом указывался для события request
![alt](https://pp.userapi.com/c845417/v845417963/871b5/SpAro7eejoU.jpg)
