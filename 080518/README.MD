# Создание	клиентского	роутера
Клиентский	роутер	позволит	нам	вводить в	адресную	строку	браузера	URL,	что	приведёт	к	смене	«страниц»	в	браузере,	создающей	у пользователя	такое	же	впечатление,	как	когда	веб-документы	загружаются	с	сервера.	
### 1.Инициализируем проект
`mkdir router_project`  
`cd router_project`
### 2. Клонируем репозиторий https://github.com/GossJS/reactDemo2018.git в папку с проектом 
### 3. Устанавливаем зависимость react-router-dom
`yarn add react-router-dom`
### 4. Из файла ./src/index.jsx вынесем звёзды и счётчик в отдельный файл Counter.jsx  
Counter.jsx :
```javascript
import React, { Component as C } from 'react';
class Counter extends C {
constructor(props) {...}
plus() {...}
render() {...}
}
const Stars = ({ length }) => <span>...</span>;
export default Counter;
```
Вот что остается в index.jsx :
```javascript
import React from 'react';
import { render as r } from 'react-dom';
import Counter from './Counter';
r(
<div><Counter stars="3" />
<Counter stars="10" />
</div>,
document.querySelector('.cont'),
);
```
### 5. Вводим App - компонент, играющий роль приложения, и оборачиваем его в BrowserRouter. Таким образом, функциональность	роутинга	будет	реализована	за	счёт	помещения	приложения	в	контекст	маршрутизатора.
```javascript
import React from 'react';
import { render as r } from 'react-dom';
import { BrowserRouter } from 'react-router-dom';
import Counter from './Counter';
const App = () => (
<div><Counter stars="3" />
<Counter stars="10" />
</div>);
r(
<BrowserRouter><App /></BrowserRouter >,
document.querySelector('.cont'),
);
```
### 6.Создаем Map.jsx	и	Gallery.jsx
Строим карту с помощью яндекс-конструктора https://yandex.ru/map-constructor/. Я построила путь от входа на территорию Герценовского университета до первого корпуса, в котором проходит большинство наших пар.
![](https://github.com/arinasaf11/router080518/blob/master/Screenshot_3.png?raw=true)  
Map.jsx:
```javascript
import React from 'react'; 
const Map = () => ( 
<div> 
<h1>Карта</h1> 
 <iframe src="https://yandex.ua/map-widget/v1/?um=constructor%3A6259abeac2e0e20613e5986677af36c1925adf2cf1cbd30539a93ec975c664b1&amp;source=constructor" width="587" height="316" frameborder="0"></iframe> 
</div> 
); 
export default Map;
```
Gallery.jsx:
```javascript
import React from 'react';

const Gallery = () =>
(<div><h1>Галерея</h1><p>Рисунки</p><img src="http://competitions.archplatforma.ru/imgs/users/rabots/22653/biggest/file4287929112.jpg" width="545" height="662" alt=""/></div>
);

export default Gallery;
```
### 7.Делим пространство «контейнера»  
Делим на :
• Menu - ту	часть,	где	находятся	пункты меню(ссылки-кнопки,	позволяющие	
переходить	от	фрейма	к	фрейму и	имеющие	условный	атрибут	target="имя_фрейма")
• Content - ту	часть,	где	располагается	сменный	контент,	т.е.	иными	словами,	происходит	рендеринг	маршрутов.
```javascript
import React from 'react';
import { render as r } from 'react-dom';
import { BrowserRouter, Switch, Route, Link } from 'reactrouter-dom';
import Counter from './Counter';
import Map from './Map';
import Gallery from './Gallery';
const Content = () => (
<main>
<Switch>
<Route exact path="/" component={Map} />
<Route path="/gallery" component={Gallery} />
<Route path="/counter" component={Counter} />
</Switch>
</main>
);
const Menu = () => (
<header>
<nav>
<ul>
<li><Link to="/">Карта</Link></li>
<li><Link to="/gallery">Галерея</Link></li>
<li><Link to="/counter">Отзывы</Link></li>
</ul>
</nav>
</header>
);
const App = () => (
<div><Menu /><Content />
</div>);
r(
<BrowserRouter><App /></BrowserRouter>,
document.querySelector('.cont'),
);
```
### 8.Устанавливаем недостающие зависимости (выводились ошибки при запуске файла)
`yarn add web-pack-server`  
`yarn add express`  
`yarn add react-router-dom`
### 9. Запускаем проект в командной строке `yarn run build` и открываем в браузере `localhost:1234`
![](https://github.com/arinasaf11/router080518/blob/master/Screenshot_1.png?raw=true)
![](https://github.com/arinasaf11/router080518/blob/master/Screenshot_2.png?raw=true)
