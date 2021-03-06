```
title: "Использование клавиатуры"
apiPath: input/keyboard/FlxKeyboard.html
```

Ввод с клавиатуры в HaxeFlixel предоставляется с помощью класса `FlxKeyboard` и фронтенда `FlxG.keys`.

## Список клавиш

Объект `FlxKeyList` содержит значение `Bool` для каждой клавиши на клавиатуре. Значения хранятся как массив, вы можете легко обращаться к ним с помощью специальных переменных экземпляра, указанных после клавиши. Полный список возможных имен клавиш указан в [документации `FlxKeyList`](http://api.haxeflixel.com/flixel/input/keyboard/FlxKeyList.html).

`FlxKeyboard` использует три списка клавиш: `pressed`, `justPressed` и `justReleased` для отслеживания нажатий. Список `pressed` содержит значения `true` для всех клавиш, которые нажаты в данный момент. Список `justPressed` содержит значения `true` только для тех клавиш, которые были нажаты после истечения последнего кадра. 

Пример использования:

``` haxe
override public function update(elapsed:Float):Void
{
	if (FlxG.keys.pressed.UP)
	{
		// Клавиша ВВЕРХ нажата
		// Этот код будет выполняться каждый кадр, пока клавиша будет нажатой
	}
	
	if (FlxG.keys.justPressed.LEFT)
	{
		// Клавиша ЛЕВО только что была нажата (в прошлом кадре была не нажата)
		// Этот код выполнится только в кекущем кадре, сразу после того как кнопка была нажата
	}
	
	if (FlxG.keys.justReleased.LEFT)
	{
		// Клавиша ЛЕВО только что была отпущена
		// Этот код выполнится только в кекущем кадре, сразу после того как кнопка была отпущена
	}

	super.update(elapsed);
}
```

## Проверка нажатия нескольких клавиш

Вы можете проверить нажатие сразу нескольких клавиш используя методы `anyPressed()`, `anyJustPressed()` и `anyJustReleased()` из `FlxKeyboard`. Это позволяет вам забиндить несколько клавиш для одного действия. Например управление движением персонажа через WASD либо стрелками. Эти методы принимают массив имен `String` и возвращают true, если хотя бы одна из этих клавиш удовлетворяет требуемому условию. 

``` haxe
override public function update(elapsed:Float):Void
{
	if (FlxG.keys.anyPressed([LEFT, A]))
	{
		// Движемся влево
	}
	
	if (FlxG.keys.anyPressed([RIGHT, D]))
	{
		// Движемся вправо
	}

	super.update(elapsed);
}
```

### Условные выражения

Для общей информации по условным выражениям ознакомтесь с [этой страницей](http://haxeflixel.com/documentation/compiler-conditionals/).

* ### `FLX_NO_KEYBOARD`

	Этот флаг позволяет вам полностью отключить любой код, который завязан на вводе с клавиатуры (например для мобильных платформ). Поэтому в шаблоне добавлена конструкция `if="mobile"` в настройках проекта `Project.xml`.
