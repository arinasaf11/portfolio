# I. Создание веб-приложения с помощью node.js с использованием серверного шаблонизатора
Цель: создать серверное приложение, которое получает массив объектов, каждый из которых имеет свойство login, из адреса https://kodaktor.ru/j/users и использует шаблон pug для вывода в веб-страницу списка этих логинов.  
### 1.Инициализируем проект
`mkdir express_project`  
`cd express_project`  
`curl -s https://kodaktor.ru/g/eslint_exec`
### 2.Устанавливаем	фреймворк	express и	шаблонизатор	pug, а	также	инструмент	axios
`yarn add express pug	axios`
### 3.Устанавливаем nodemon
`yarn add --dev nodemon`
### 4.Добавляем в файл package.json раздел scripts с командой start:
![](https://github.com/arinasaf11/express200318/blob/master/Screenshot_1.png?raw=true)
### 5.Создаем файл index.js в папке ./src
```javascript
const express = require('express');  
const PORT = 4321; 
const app = express(); 
app 
.get(/hello/, r => r.res.end('Hello world!')) 
.use(r => r.res.status(404).end('Still not here, sorry!')) 
.use((e, r, res, n) => res.status(500).end(`Error: ${e}`)) 
.set('view engine', 'pug') 
.listen(process.env.PORT || PORT, () => console.log(process.pid));
```
### 6.Создаем файл list.pug в папке ./views
![](https://github.com/arinasaf11/express200318/blob/master/Screenshot_2.png?raw=true)
### 7.Импортируем метод get из зависимости axios: `const { get } = require('axios')`, создаем асинхронный обработчик маршрута users, используем метод render объекта Response для связывания шаблона list.pug с данными, полученными из адреса https://kodaktor.ru/j/users
![](https://github.com/arinasaf11/express200318/blob/master/Screenshot_3.png?raw=true)
### 8. Результат в браузере
![](https://github.com/arinasaf11/express200318/blob/master/result.jpg?raw=true)
