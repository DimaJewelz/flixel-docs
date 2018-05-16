```
title: "Список отображения в Flixel"
```
Список отображения в Flixel представляет собой специальную структуру для отображения спрайтов в вашей игре.

#### `FlxSprite` != `flash.display.Sprite`

Во Flash [список отображения](http://help.adobe.com/en_US/as3/dev/WS5b3ccc516d4fbf351e63e3d118a9b90204-7e58.html) строится на зависимости родительский [объект](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/display/DisplayObjectContainer.html) -> дочерний [объект](http://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/display/DisplayObject.html). `Sprite` расширяет функционал обычного `DisplayObject`. Порядок отображения (глубина) детей в родительском объекте легко может быть изменена.

Для начинающих изучение Flixel важно помнить, что `FlxSprite` отличается от стандартного `Sprite` во Flash. `FlxSprite` не поддерживает событийную модель как `Sprite`, поэтому `addEventListener()` не доступен для него.

У Flixel есть свой независимый список отображения, в котором происходит рендер всех `FlxSprite` в одном классическом `DisplayObject` для каждой камеры `FlxCamera`. Поэтому нельзя добавить `flash.display.Sprite` в `FlxState` и также нельзя добавить `FlxSprite` на `flash.display.Stage`.

На диаграмме показаны экранные объекты, используемые во Flixel. Обратите внимание, что вы можете помещать экранные объекты выше или ниже камеры. Для этой цели рекомендуется использовать `FlxG.addChildBelowMouse()` и `FlxG.removeChild()`.

<img src="../images/02_handbook/flixel-display-list.png" style="max-width:400px" />
