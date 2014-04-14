# TabContent

Класс описывающий содержимое вкладок.

###Оглавление


<a href="#Публичные-свойства">`Публичные свойства`</a>
* <a href="#isinited">`isInited`</a>
* <a href="#startel">`startEl`</a>
* <a href="#lazyparsebinds">`lazyParseBinds`</a>

<a href="#Публичные-методы">`Публичные методы`</a>
* <a href="#init">`init()`</a>
* <a href="#focus">`focus()`</a>
* <a href="#blur">`blur()`</a>




##Публичные свойства

###`isInited`

*Boolean*: показывает инициализирована ли вкладка. Инициализация происходит при первом вызове `focus` (lazy init)

1. `true`: инициализирован
2. `false`: не инициализирован

* * *


###`startEl`

*jQuery*: элемент или селектор jQuery на который перейдет фокус после вызова `focus()`

* * *

###`lazyParseBinds`

*Boolean*: если установлен в `true` при первом вызове `focus()` будет вызван метод `ViewModel.parse()` который активирует data binding

Значение по умолчанию: `false`

* * *


## Публичные методы

###`init()`

Вызывается первый раз при вызове `focus()`, должен быть переопределен в дочернем классе. По умполчанию ничего не делает.

#### Примеры
```js
var tabView1 = TabContent.create({
    el: '#tab1',
    init: function(){
        this.$('.loader').show();
    }
});
```

* * *

###`focus()`

Вызывается из класса TabsHead после клика по вкладке. Может быть переопределена для дополнительных действий с учетом вызова `this._super()`
По умолчанию вызывает при первом вызове `init()`. И `parse()` в случае если выставлен флаг `lazyParseBinds`

* * *


###`blur()`

Вызывается из класса TabsHead после клика по вкладке перед вызовом другой TabContent. По умолчанию ничего не делает. Может быть переопределена в дочернем классе.

* * *