```
title: "Управление с помощью геймпада"
apiPath: input/gamepad/index.html
```

Ввод с помощью геймпада в HaxeFlixel обеспечивается с помощью классов `FlxGamepad`, `InputFrontEnd` и фронтенда `FlxG.gamepads`. 

Т.к. геймпады имеют большое кол-во производителей, их коды клавиш в HaxeFlixel API могут отличаться в зависимости от модели. HaxeFlixel предоставляет сопоставления, которые связывают кнопки и стики с общими идентификаторами для удобного использования. Сопоставления доступны для:

- XInput (Xbox 360, Xbox One, etc)
- PS4
- OUYA
- Logitech
- WiiRemote
- Mayflash WiiRemote
- MFi
- PS Vita

Для большинства геймпадов HaxeFlixel автоматически определяет модель и подгоняет API ввода под общую "универсальную" модель геймпада, основанную на макете Xbox 360. Остальные кнопки, зависящие от конкретной модели геймпада, также остаются доступны для вызова напрямую.

Ниже пример логики с использованием API универсального геймпада:

``` haxe
import flixel.FlxG;
import flixel.FlxState;
import flixel.input.gamepad.FlxGamepad;

class PlayState extends FlxState
{
    override public function update(elapsed:Float):Void 
    {
        super.update(elapsed);

        // Важно: может быть null, если геймпад не подключен
        var gamepad:FlxGamepad = FlxG.gamepads.lastActive;
        if (gamepad != null)
        {
            updateGamepadInput(gamepad);
        }
    }

    function updateGamepadInput(gamepad:FlxGamepad):Void
    {
        if (gamepad.pressed.A)
        {
            trace("Нажата нижняя кнопка контроллера.");
        }
		
        if (gamepad.analog.justMoved.LEFT_STICK_X)
        {
			trace("Левый стик контроллера был подвинут по оси x.");
        }
    }
}
```

В данном случае ```gamepad.pressed.A``` проверяет, нажата ли нижняя кнопка. На контроллере PS4  это будет кнопка "X", на контроллере XBox 360 или XBox One это будет кнопка "А".

Также синтаксис ```gamepad.pressed.A``` - это сокращение от ```gamepad.pressed.check(FlxGamepadInputID.A)```. Последний синтаксис удобно использовать в случае если вам нужно проверить переменную (в случае когда пользователь меняет управление).

Если вы хотите проверить ввод с определенного устройства, используйте функцию ```checkRaw```, например так: ```gamepad.pressed.checkRaw(PS4ID.X)```.

Вводы, характерные для конкретного устройства могут быть найдены в пакете ```flixel.input.gamepad.id```.

Если вы хотите поддерживать контроллер, для которого HaxeFlixel не предоставляет ID, следующие методы класса `FlxGamePad` будут полезны:

Возвращает значение ```FlxGamepadInputID``` для универсальной модели геймпада:
- `firstPressedButtonID()`
- `firstJustPressedButtonID()`
- `firstJustReleasedButtonID()`

Возвращает ID ввода, характерного для конкретного устройства:
- `firstPressedButtonRawID()`
- `firstJustPressedButtonRawID()`
- `firstJustReleasedButtonRawID()`

### Условные выражения

``` haxe
FLX_NO_GAMEPAD
```

HaxeFlixel включает в себя [условное выражение](http://haxeflixel.com/documentation/haxeflixel-conditionals/) для отключения использования геймпадов с целью оптимизации. Полезно в случае если вы разрабатываете под мобильную платформу, либо если ваша игра не рассчитана для использования геймпадов.
