# Анализ открытия страницы в Chrome DevTools

Сделать в Chrome DevTools анализ открытия страницы <https://www.rigla.ru>. Открывать Chrome в режиме инкогнито. Использовать вкладки Network, Performance, Coverage.

## Содержание

- [Slow версия](./Slow/README.md)
- [Подготовка](#подготовка)
- [Network](#network)
- [Performance](#performance)
- [Coverage](#coverage)

## Подготовка

- Использовать URL <https://www.rigla.ru>
- Открывать URL в режиме инкогнито <https://support.google.com/chrome/answer/95464> с отключенными расширениями браузера, чтобы они не искажали результаты
- На вкладке Network отключить кэш (Disable cache) — это эмулирует первый заход пользователя на страницу, когда у него пустой кэш

## Network

[Вернуться к содержанию](#содержание)

### Описание Network

1. [Записать и сохранить в HAR архив профиль загрузки ресурсов при открытии страницы](./network/www.rigla.ru.har)
2. Найти неоптимальные места:
   - [Дублирование ресурсов](#дублирование-ресурсов)
   - [Лишний размер ресурса](#лишний-размер-ресурса)
   - [Медленно загружающиеся ресурсы](#медленно-загружающиеся-ресурсы)
   - [Ресурсы, блокирующие загрузку](#ресурсы-блокирующие-загрузку)
3. При описании найденных неоптимальных мест делать скриншот соответствующего участка панели Network, чтобы было понятно, что именно имеется в виду

#### Дублирование ресурсов

![](./Network/repeatingElements/1.png)

![](./Network/repeatingElements/2.png)

![](./Network/repeatingElements/3.png)

#### Лишний размер ресурса

Неоптимизированные изображения

![](./Network/extraSize/images.png)

#### Медленно загружающиеся ресурсы

![](./Network/slowLoading/slow.png)

#### Ресурсы, блокирующие загрузку

![](./Network/blocking/resources.png)

## Performance

[Вернуться к содержанию](#содержание)

### Описание Performance

1. [Записать и сохранить в файл профиль загрузки страницы](./performance/Trace-20240620T000139.json)
2. Измерить время в миллисекундах от начала навигации до событий:
   - [First Paint (FP)](#first-paint)
   - [First Contentful Paint (FCP)](#first-contentful-paint)
   - [Largest Contentful Paint (LCP)](#largest-contentful-paint)
   - [DOM Content Loaded (DCL)](#dom-content-loaded)
   - [Load](#load)
3. [Определить, на каком DOM-элементе происходит LCP](#dom-элемент-lcp)
4. [Измерить, сколько времени в миллисекундах тратится на разные этапы обработки документа (Loading, Scripting, Rendering, Painting)](#время-на-разные-этапы-обработки-документа)

#### First Paint

Timestamp 896.9 ms

![](./Performance/First-Paint.png)

#### First Contentful Paint

Timestamp 896.9 ms

![](./Performance/First-Contentful-Paint.png)

#### Largest Contentful Paint

Timestamp 1930.3 ms

![](./Performance/Largest-Contentful-Paint.png)

#### DOM Content Loaded

Timestamp 472.9 ms

![](./Performance/DOMContentLoaded.png)

#### Load

Timestamp 22324.6 ms

![](./Performance/Load.png)

#### DOM-элемент LCP

![](./Performance/DOM-elem-LCP.png)

#### Время на разные этапы обработки документа

![](./Performance/Time.png)

## Coverage

[Вернуться к содержанию](#содержание)

### Описание Coverage

1. [Сохранить скриншот вкладки после загрузки страницы](#скриншот-coverage)
2. [Измерить в килобайтах объём неиспользованного CSS в ходе загрузки страницы](#объём-неиспользованного-css)
3. [Измерить в килобайтах объём неиспользованного JS в ходе загрузки страницы](#объём-неиспользованного-js)

#### Скриншот Coverage

![](./Coverage/Coverage.png)

#### Объём неиспользованного CSS

~45,4 Кб

![](./Coverage/CSS_unused.png)

#### Объём неиспользованного JS

~3600 Кб

![](./Coverage/JS_unused.png)

