```
title: "Использование Haxelib"
```

Haxelib это менеджер пакетов и утилита, которая устанавливается вместе с Haxe. Ниже примеры наиболее часто используемых команд, полный список [доступен тут](http://haxe.org/doc/haxelib/using_haxelib).

### Установка библиотеки

Установка библиотеки Haxelib с [lib.haxe.org](http://lib.haxe.org/):

```
haxelib install <library>
```

Установка бибилотеки Haxelib через Git:

```
haxelib git <library> <url> <branch>
```

_Обратите внимание: `haxelib git` подключает dev версию это библиотеки, которая запрещает использование команды `haxelib set`. Используйте команду `haxelib dev <library>` чтобы отключить это._

Обновление ваших Haxelib библиотек, включая те, который были установлены с помощью Git:

```
haxelib upgrade
```

Переключиться на другую версию библиотеки:

```
haxelib set <library> <version>
```

Удалить библиотеку:

```
haxelib remove <library>
```

### Обновление самой Haxelib

Чтобы убедиться, что вы используете последнюю версию Haxelib, вы можете запустить команду `selfupdate`.

```
haxelib selfupdate
```
