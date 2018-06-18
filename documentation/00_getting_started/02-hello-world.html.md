```
title: "Hello World"
```

"Hello World" это [общий пример](http://en.wikipedia.org/wiki/Hello_world_program) начала программирования. В этом разделе мы покажем как отобразить на экране текст Hello World с помощью `FlxText`. Вы можете скомпилировать этот пример под любую поддерживаемую платформу.

Убедитесь что вы установили Flixel, а также настроили команды `lime` and `flixel`, что было [описано ранее](/documentation/install-haxeflixel/).

### Создание нового проекта HaxeFlixel

HaxeFlixel требует базовую структуру файлов для любого проекта, которую вы можете автоматически создать, используя команду `template` (короткая версия - `tpl`).

``` bash
flixel tpl -n "HelloWorld"
```

Вы увидите новую папку "HelloWorld", в которой автоматически были созданы все необходимые файлы для проекта.

### Добавление текста "Hello World" `FlxText`

Чтобы добавить текст, откройте файл `PlayState.hx` в созданной директории `source`. Его содержание должно выглядеть вот так:

``` haxe
package;

import flixel.FlxState;

class PlayState extends FlxState
{
	override public function create():Void
	{
		super.create();
	}

	override public function update(elapsed:Float):Void
	{
		super.update(elapsed);
	}
}
```

Все что вам необходимо сделать, это добавить три строчки кода в функцию `create()` и сохранить файл:

``` haxe
var text = new flixel.text.FlxText(0, 0, 0, "Hello World", 64);
text.screenCenter();
add(text);
```

Этот код создает новое текстовое поле `FlxText` с размером шрифта `64`, центрирует его на экране, и добавляет его (`add()`) в список отображения .

### Тестирование проекта

Теперь вернемся к командной строке - сейчас мы можем скомпилировать проект. Без запуска команды `lime setup`, вы можете компилировать под таргеты HTML5, Flash и Neko из коробки, используя следующие команды:

``` bash
lime test html5
lime test flash
lime test neko
```

Если что-то в этом уроке вызвало затруднения, обратитесь в любой [канал сообщества](/documentation/community/) для помощи.

![](../images/00_getting_started/hello-world.png)
