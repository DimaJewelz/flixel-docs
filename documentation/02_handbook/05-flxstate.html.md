```
title: "FlxState"
apiPath: FlxState.html
```

`FlxState` это основа для уровней и экранов меню вашей игры. Каждое состояние описывается в отдельной структуре "state". `FlxState` служит для организации игровых объектов в текущем игровом состоянии. Например, если вы создаете первый уровень для игры, то в `FlxState` будет код только для этого уровня, а не для всей игры. Также при смене состояний, память очищается, что помогает избегать переполнения и утечки памяти. Обычно используют отдельные состояния `FlxState` для каждого уровня и меню.

<img src="../images/02_handbook/flixel-state-0.png" width="100%" />

В каждом `FlxState` отображаются все спрайты, которые были добавлены в него.

<img src="../images/02_handbook/flixel-state-1.png" width="100%" />

### Важные методы

#### create()

Метод, в котором вы создаете и настраиваете все объекты для этого состояния. Например тайлмапы для уровня, графику для игрового персонажа, размещаете и инициализируете врагов. Этот метод вызывается до первой отрисовки экрана.

#### add(object:FlxBasic)

Метод, в котором вы добавляете спрайты и тайлмапы в список отображения. Метод схож с методом `addChild()` в OpenFL.

#### remove(object:FlxBasic)

Метод, в котором вы удаляете спрайты из списка отображения. Все, что вы удалите, все еще будет находиться в памяти, и в дальнейшем вы сможете использовать эти объекты. Если вы не хотите использовать эти объекты в дальнейшем, обнулите ссылку на этот объект и он удалится из памяти.

#### update(elapsed:Float)

Код в этом методе выполняется каждый игровой фрейм. Здесь необходимо настроить ввод пользовательских действий, движение и практически всю игровую логику уровня.

``` haxe
package;

import flixel.FlxState;

class FlxExampleState extends FlxState
{
	override public function create():Void
	{
		//создание игровых объектов
	}

	override public function update(elapsed:Float):Void
	{
		//вызов базового метода для обновления состояния базового класса
		super.update(elapsed);
	}
}
```

Ниже пример простого игрового состояния:

``` haxe
package;

import flixel.tile.FlxTilemap;
import flixel.FlxObject;
import flixel.FlxG;
import flixel.FlxSprite;
import flixel.FlxState;
import flixel.graphics.FlxGraphic;

class FlxExampleState extends FlxState
{
	var wizard:FlxSprite;
	var level:FlxTilemap;

	override public function create():Void
	{
		//создание игрового персонажа
		wizard = new FlxSprite(200, 200, 'assets/player.png');
		wizard.maxVelocity.set(80, 200);
		wizard.acceleration.y = 200; // gravity
		wizard.drag.x = wizard.maxVelocity.x * 4;
		add(wizard);

		//создание графики уровня 
		level = new FlxTilemap();
		level.loadMap('assets/level.csv', FlxGraphic.fromClass(GraphicAuto), 0, 0, AUTO);
		add(level);
	}

	override public function update(elapsed:Float):Void
	{
		//логика управления персонажем с помощью клавиатуры
		wizard.acceleration.x = 0;

		if (FlxG.keys.pressed.LEFT)
		{
			wizard.acceleration.x = -wizard.maxVelocity.x * 4;
		}
		if (FlxG.keys.pressed.RIGHT)
		{
			wizard.acceleration.x = wizard.maxVelocity.x * 4;
		}
		if (FlxG.keys.justPressed.SPACE && wizard.isTouching(FlxObject.FLOOR))
		{
			wizard.velocity.y = -wizard.maxVelocity.y / 2;
		}
		super.update(elapsed);
	}
}
```

 
