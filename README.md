# Сетка 23g

## Установка через composer

И сетка и набор микро-классов не включены в список composer репозиториев, по этому придется их подключить вручную:
```json
{
	"repositories": [
		{
			"type": "git",
			"url": "https://github.com/Vallefor/23g.git"
		},
		{
			"type": "git",
			"url": "https://github.com/Vallefor/css-framework.git"
		}

	],
    "require": {
		"upriver/23g":				"2.0.*",
		"upriver/css-framework":	"1.0.*"
    }
}
```

## Подключение CSS для EVA CMS:

```php
	<link type="text/css" href="<?=evaLink::getEva()->addModTimeToPath("/vendor/upriver/23g/center/grid.css")?>" rel="stylesheet" />

    <link type="text/css" href="<?=evaLink::getEva()->addModTimeToPath("/vendor/upriver/23g/center/s-grid-center.css")?>" rel="stylesheet" />
    <link type="text/css" media="screen and (min-width: 768px)" href="<?=evaLink::getEva()->addModTimeToPath("/vendor/upriver/23g/center/m-grid-center.css")?>"  rel="stylesheet" />
    <link type="text/css" media="screen and (min-width: 1024px)" href="<?=evaLink::getEva()->addModTimeToPath("/vendor/upriver/23g/center/h-grid-center.css")?>"  rel="stylesheet" />
    
    <link type="text/css" href="<?=evaLink::getEva()->addModTimeToPath("/vendor/upriver/23g/general/s-add.css")?>" rel="stylesheet" />
    <link type="text/css" media="screen and (min-width: 768px)" href="<?=evaLink::getEva()->addModTimeToPath("/vendor/upriver/23g/general/m-add.css")?>"  rel="stylesheet" />
    <link type="text/css" media="screen and (min-width: 1024px)" href="<?=evaLink::getEva()->addModTimeToPath("/vendor/upriver/23g/general/h-add.css")?>"  rel="stylesheet" />
    
    <link type="text/css" media="screen and (max-width: 767px)" href="<?=evaLink::getEva()->addModTimeToPath("/vendor/upriver/23g/general/invert-s-grid-center.css")?>"  rel="stylesheet" />
    <link type="text/css" media="screen and (max-width: 1023px) and (min-width: 768px)" href="<?=evaLink::getEva()->addModTimeToPath("/vendor/upriver/23g/general/invert-m-grid-center.css")?>"  rel="stylesheet" />
    <link type="text/css" media="screen and (min-width: 1024px)" href="<?=evaLink::getEva()->addModTimeToPath("/vendor/upriver/23g/general/invert-h-grid-center.css")?>"  rel="stylesheet" />
```

или

```php
	<link type="text/css" href="<?=evaLink::getEva()->addModTimeToPath("/vendor/upriver/23g/23g-center.css");?>" rel="stylesheet" />
```

## Подключение CSS в обычном режиме

```html
    <link type="text/css" href="/vendor/upriver/23g/center/s-grid-center.css" rel="stylesheet" />
    <link type="text/css" media="screen and (min-width: 768px)" href="/vendor/upriver/23g/center/m-grid-center.css"  rel="stylesheet" />
    <link type="text/css" media="screen and (min-width: 1024px)" href="/vendor/upriver/23g/center/h-grid-center.css"  rel="stylesheet" />
    
    <link type="text/css" href="/vendor/upriver/23g/general/s-add.css" rel="stylesheet" />
    <link type="text/css" media="screen and (min-width: 768px)" href="/vendor/upriver/23g/general/m-add.css"  rel="stylesheet" />
    <link type="text/css" media="screen and (min-width: 1024px)" href="/vendor/upriver/23g/general/h-add.css"  rel="stylesheet" />
    
    <link type="text/css" media="screen and (max-width: 767px)" href="/vendor/upriver/23g/general/invert-s-grid-center.css"  rel="stylesheet" />
    <link type="text/css" media="screen and (max-width: 1023px) and (min-width: 768px)" href="/vendor/upriver/23g/general/invert-m-grid-center.css"  rel="stylesheet" />
    <link type="text/css" media="screen and (min-width: 1024px)" href="/vendor/upriver/23g/general/invert-h-grid-center.css"  rel="stylesheet" />
```
или
```html
	<link type="text/css" href="/vendor/upriver/23g/23g-center.css" rel="stylesheet" />
```

## Инициализация

Необходимо открыть 3 дива: 
```html
<div class="first">
    <div class="second">
        <div class="third">
            <!-- место для колонок -->
            <div class="cb"></div>
        </div>
    </div>
</div>
```

Внутри можно использовать колонки. У каждой колонки должен быть класс *column* 
```html
    <div class="column"></div>
```

Перед закрывающимся *.third* обязательно нужно исполькловать *clear:both;* Это связано с тем, что все колонки имеют свойство *float: left;* 

Список микро-классов можно посмотреть тут:
https://github.com/Vallefor/css-framework/blob/master/css/framework.css



## Префиксы

s - small - маленький экран (смартфоны, ширина < 768 пикселей)

m - medium - средний экран (портретный режим планшета, ширина: 768-1023)

h - high - большой экран (экран десктоп компьютера или ландшафтный режим планшета, ширина >= 1024)

```html
    <div class="column s-width-23 m-width-11 h-width-7"></div>
```

В данном примере, колонка будет иметь ширину 23 колонки на смартфоне, 11 колонок на портретном режиме планшета и 7 колонок, на мониторе компьютера.
 
Нужно иметь ввиду, что классы с префиксами загружаются по очереди. То есть на самом большом экране, по очереди сработают все префиксы и останется активным последний. Если колонка должна быть шириной в 23 колонки на всех экранах, достаточно использовать только самый первый префикс:
```html
    <div class="column s-width-23"></div>
```

Запрещается давать колонке дополнительные паддинги или марджины любыми средствами - это собьет сетку, если нужны дополнительные отступы - используйте внутренний div:
```html
    <div class="column s-width-23">
        <div style="margin:20px;"></div>
    </div>
```

## Сдвиг колонок

Для сдвига колонок используеются классы вида [prefix]-push-[num], например m-push-12 - сдвиг колорннки, на 12 колонок при размере экрана medium.

Для того, чтоб отобразить на экране 2 одинаковых колонки, вторую колонку нужно сдвинуть на 11 колонок + 1 колонка на отступ. Получаем:
```html
<div class="first">
    <div class="second">
        <div class="third">
            <div class="column s-width-11 s-push-0"></div>
            <div class="column s-width-11 s-push-12"></div>
            <div class="cb"></div>
        </div>
    </div>
</div>
```

## invert префиксы
invert префиксы, в отличае от обычных, сработают только на определенном размере монитора. Например:
```html
    <div class="invert-m-cb"></div>
```
clear:both; - сработает только при разрешении экрана - medium.

invert-префиксы можно комбинировать
```html
    <div class="invert-m-cb invert-s-cb"></div>
```
clear:both; - сработает только при разрешении экрана - medium и small.


# Набор готовых решений

## 6 одинаковых колонок
```html
<div class="first">
    <div class="second">
        <div class="third">
            <div class="column s-width-11 s-push-0 m-width-7 h-width-3"> 1 </div>
            <div class="column s-width-11 s-push-12 m-width-7 m-push-8 h-width-3 h-push-4"> 2 </div>
            <div class="invert-s-cb"></div>
            <div class="column s-width-11 s-push-0 m-width-7 m-push-16 h-push-3 h-push-8"> 3 </div>
            <div class="invert-s-cb invert-m-cb"></div>
            <div class="column s-width-11 s-push-12 m-width-7 h-width-3 h-push-12"> 4 </div>
            <div class="invert-s-cb"></div>
            <div class="column s-width-11 s-push-0 m-width-7 m-push-8 h-width-3 h-push-16"> 5 </div>
            <div class="column s-width-11 s-push-12 m-width-7 m-push-16 h-width-3 h-push-20"> 6 </div>
            <div class="cb"></div>
        </div>
    </div>
</div>
```

## 4 одинаковых колонки
```html
<div class="first">
    <div class="second">
        <div class="third">
            <div class="column s-width-23 s-push-0 m-width-11 h-width-5"></div>
            <div class="invert-s-cb"></div>
            <div class="column s-width-23 s-push-0 m-width-11 m-push-12 h-width-5 h-push-6"></div>
            <div class="invert-s-cb invert-m-cb"></div>
            <div class="column s-width-23 s-push-0 m-width-11 h-width-5 h-push-12"></div>
            <div class="invert-s-cb invert-m-cb"></div>
            <div class="column s-width-23 s-push-0 m-width-11 m-push-12 h-width-5 h-push-18"></div>
            <div class="cb"></div>
        </div>
    </div>
</div>
```

## 3 одинаковых колонки
```html
<div class="first">
    <div class="second">
        <div class="third">
            <div class="column s-width-23 s-push-0 m-width-11 h-width-7"></div>
            <div class="invert-s-cb"></div>
            <div class="column s-width-23 s-push-0 m-width-11 m-push-12 h-width-7 h-push-8"></div>
            <div class="invert-s-cb invert-m-cb"></div>
            <div class="column s-width-23 s-push-0 m-width-11 m-push-6 h-width-7 h-push-16"></div>
            <div class="cb"></div>
        </div>
    </div>
</div>
```

```html
<div class="first">
    <div class="second">
        <div class="third h-3-in-row m-2-in-row s-1-in-row">
            <div class="column"></div>
            <div class="column"></div>
            <div class="column"></div>
            <div class="column"></div>
			<div class="column"></div>
			<div class="column"></div>
            <div class="cb"></div>
        </div>
    </div>
</div>
```

## Фон на несколько колонок
```html
<div class="first">
    <div class="second">
        <div class="third">
            <div class="pa h100 column s-width-11" style="background: #afafaf;"></div>
            <div class="column s-width-5 pr">
                text
            </div>
            <div class="column s-width-5 s-push-11 pr">
                text
            </div>
            <div class="cb"></div>
        </div>
    </div>
</div>
```

# Колонки встык
Для этого нужно добавить любому родительскому элементу класс [s,m,h]-grid-to-[2-5], например
* s-grid-to-2 - сделает 2 одинаковые колоки, шириной по 50% (начиная с размера s)
* m-grid-to-4 - сделает 4 одинаковые колоки, шириной по 25% (начиная с размера m)

```html
<div class="first">
    <div class="second">
        <div class="third s-grid-to-2 m-grid-to-4">
            <div class="column"></div>
            <div class="column"></div>
            <div class="column"></div>
        </div>
    </div>
</div>
```

Так же, допустимо делать такие колонки, без инициализации сетки, но в этом случае, класс column, нужно заменить на fullColumn

```html
<div class="s-grid-to-2 m-grid-to-4">
    <div class="fullColumn"></div>
    <div class="fullColumn"></div>
    <div class="fullColumn"></div>
</div>
```