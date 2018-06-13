```
title: "Установка HaxeFlixel"
```

Для установки последней стабильной версии HaxeFlixel, откройте командную строку и выполните следующие команды [Haxelib](http://lib.haxe.org/):

``` bash
haxelib install lime
haxelib install openfl
haxelib install flixel
```

После завершения установки, вы сможете компилировать игры под платформы HTML5, Flash и Neko прямо из коробки.

Для легкой установки дополнительных библиотек в один шаг (дополнений, ui, демо, инструментария, шаблонов...), просто выполните:

```bash
haxelib run lime setup flixel
```

### Установка `lime`

```bash
haxelib run lime setup
```

Это делает доступным команду `lime` (алиас для `haxelib run lime`).

Для компиляции под десктоп и мобильные таргеты, вы должны убедиться, что запустили соответствующие команды `lime setup` 
Каждая из них указана в 
[OpenFL platform docs](http://www.openfl.org/learn/docs/advanced-setup/).

### Установка `flixel` 

Выполните две команды для установки [flixel-tools](http://haxeflixel.com/documentation/flixel-tools/) (требуется, помимо прочего, для шаблонов проектов):

``` bash
haxelib install flixel-tools
haxelib run flixel-tools setup
```

### Обновление HaxeFlixel

Если выпущены новые версии HaxeFlixel, и вы хотите обновиться до них, используйте следующую команду:

``` bash
haxelib update flixel
```

Если вы хотите обновить например `flixel-addons`, просто замените `flixel` на `flixel-addons`.

Чтобы быть в курсе новых релизов, вы можете подписаться на наш Twitter [@HaxeFlixel](https://twitter.com/HaxeFlixel) или наш блог [Blog](http://haxeflixel.com/blog/).

### Dev версия

Если вы хотите использовать код из версии в разработке [на GitHub](https://github.com/HaxeFlixel/flixel), ознакомьтесь с [инструкциями](/documentation/install-development-flixel).