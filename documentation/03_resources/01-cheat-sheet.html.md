```
title: "Шпаргалка"
```

## [FlxSprite](http://haxeflixel.com/documentation/flxsprite) (Базовый)

```haxe
package;

import flixel.FlxSprite;
import flixel.FlxG;

class MySprite extends FlxSprite
{
	public function new()
	{
		super();
	}

	override public function update(elapsed:Float):Void
	{
		super.update(elapsed);
	}
}
```


## [FlxState](http://haxeflixel.com/documentation/flxstate) (Базовый)

```haxe
package;

import flixel.FlxState;
import flixel.FlxG;

class MyState extends FlxState
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


## Switch [FlxState](http://haxeflixel.com/documentation/flxstate)

```haxe
FlxG.switchState(new MyState());
```

## Load [FlxSprite](http://haxeflixel.com/documentation/flxsprite)

```haxe
loadGraphic("assets/my_sprite.png");

// ИЛИ динамически создаем прямоугольник
makeGraphic(100, 100, 0xFFFFFFFF); // ширина, высота, цвет (шестнадцатеричный AARRGGBB)

// обновляем дефолтный хитбокс (расположенный в верхнем левом углу спрайта)
updateHitbox(); // либо offset.set(10, 5); чтобы сместить хитбокс на 10 пикселей по горизонтали и на 5 по вертикали
```

## FlxText

* **setFormat**(Font, Size, Color, Alignment)
* **setBorderStyle**(Style, Color, Size)

```haxe
import flixel.text.FlxText;
import flixel.util.FlxColor;
```

```haxe
myText = new FlxText(0, 0, 500); // x, y, ширина
myText.text = "Hello World";
myText.setFormat("assets/font.ttf", 20, FlxColor.WHITE, CENTER);
myText.setBorderStyle(OUTLINE, FlxColor.RED, 1);
```


## FlxButton

```haxe
import flixel.ui.FlxButton;
```

```haxe
myButton = new FlxButton(0, 0, "Label", myCallback);

// собственная графика
myButton.loadGraphic("assets/custom.png");
```

```haxe
function myCallback():Void
{
}
```

* **myButton.label** это `FlxText`, используйте `setFormat()` и `setBorderStyle()` для кастомизации.


## Звуковые эффекты и музыка
Если вы не изменяли пути в `Project.xml`, положите звуковые файлы в директории `assets/music` и `assets/sounds`. Звуковые файлы готовы к использованию в коде.

Обычно используют звуковые эффекты в WAV формате (44.1 kHz).

Для Flash таргета музыка должна быть в MP3 формате (44.1 kHz) и в OGG фомарте для других таргетов. Для поддержки обоих типов платформ (флеш и остальных) без внерения обоих типов файлов в финальный билд проекта, вы можете заменить тег `<assets>` в файле `Project.xml` следующими строками:

```xml
<assets path="assets" exclude="*.ogg" if="flash"/>
<assets path="assets" exclude="*.mp3" unless="flash"/>
```
Воспроизведение в коде:

```haxe
// Воспроизведение звукового эффекта используя AssetPaths
FlxG.sound.play(AssetPaths.mySound__wav);
// Воспроизведение звукового эффекта не используя AssetPaths
FlxG.sound.play("assets/sounds/mySound.wav");

// Цикличное воспроизведение музыки (только Flash таргет)
FlxG.sound.playMusic(AssetPaths.myMusic__mp3);
// Цикличное воспроизведение музыки (все таргеты, кроме Flash)
FlxG.sound.playMusic(AssetPaths.myMusic__ogg);
// Цикличное воспроизведение музыки для всех таргетов (метод getSound() добавляет .mp3 для Flash таргета и .ogg для всех остальных платформ)
FlxG.sound.playMusic(FlxAssets.getSound("assets/music/myMusic"));
```

## Ввод с клавиатуры

```haxe
// Клавиша 'A'
if (FlxG.keys.justPressed.A) {}
if (FlxG.keys.pressed.A) {}
if (FlxG.keys.justReleased.A) {}

// Проверка нажатия нескольких клавиш:
if (FlxG.keys.anyPressed([RIGHT, D])) {}
```

#### Клавиши
`ANY`

`A`...`Z`

`UP` `DOWN` `LEFT` `RIGHT`

`SPACE` `ENTER` `ESCAPE`

`ZERO` `ONE` `TWO` `THREE`...`NINE`

`F1`...`F12`
 
`ALT`
`BACKSLASH`
`BACKSPACE`
`CAPSLOCK`
`CONTROL`
`DELETE`
`HOME`
`INSERT`
`QUOTE`
`PERIOD`
`PLUS`
`MINUS`
`PAGEUP`
`PAGEDOWN`
`RBRACKET`
`GRAVEACCENT`
`TAB`
`SLASH`
`SEMICOLON`

`NUMPADZERO` `NUMPADONE` `NUMPADTWO`...`NUMPADNINE`


## Ввод с [мыши](http://haxeflixel.com/documentation/mouse)

```haxe
if (FlxG.mouse.pressed) {}
if (FlxG.mouse.justPressed) {}
if (FlxG.mouse.justReleased) {}
```

#### Координаты курсора
```haxe
// Относительно глобальной системы координат
FlxG.mouse.x;
FlxG.mouse.y;

// Относительно экрана
FlxG.mouse.screenX;
FlxG.mouse.screenY;
```

#### Колесо мыши (скролл мышью)
Значения свойство delta определяет в каком направлении было повернуто колесико мыши. Если вверх - то это св-во будет иметь положительное значение, если вниз - отрицательное. Если попорота колесика мыши в данном фрайме не было, то значение delta будет 0.

```haxe
FlxG.mouse.wheel;
```

#### Колбеки нажатия кнопки мыши, отпускания кнопки мыши, наведения курсора на объект, отведения курсора от объекта

```haxe
var clickableSprite:FlxSprite;

// ...

// регистрируем плагин в PlayState.create()
FlxMouseEventManager.init();

// ...

// регистрируем колбеки
var pixelPerfect = false;
FlxMouseEventManager.add(clickableSprite, mousePressedCallback, mouseReleasedCallback, null, null, false, true, pixelPerfect, [FlxMouseButtonID.LEFT, FlxMouseButtonID.RIGHT]);

// ...

function mousePressedCallback(sprite:FlxSprite)
{
	if (FlxG.mouse.justPressed)
	{
		// левая кнопка мыши была нажата
	}
	else if (FlxG.mouse.justPressedRight)
	{
		// правая кнопка мыши была нажата
	}
}

function mouseReleasedCallback(sprite:FlxSprite)
{
}
```

## Ввод с помощью касаний (тачей)

```haxe
for (touch in FlxG.touches.list)
{
	if (touch.justPressed) {}
	if (touch.pressed) {}
	if (touch.justReleased) {}
}
```

#### Координаты касания
```haxe
// Относительно глобальной системы координат
touch.x;
touch.y;
   
// Относительно экрана
touch.screenX;
touch.screenY;
```

* `touchPointID`: Уникальный ID касания

* `overlaps(objectOrGroup)`: Проверяет пересечение между этим касанием и объектом `FlxObject` или `FlxGroup`.


## Ввод с помощью жестов (свайпов)

"Свайпы" с помощью мыши и касаний:

```haxe
for (swipe in FlxG.swipes)
{
    // swipe.startPosition (FlxPoint)
    // swipe.endPosition (FlxPoint)
    
    // swipe.id (Int)

    // swipe.distance (Float)
    // swipe.angle (Float)
    // swipe.duration (Float)
}
```


## FlxSignal

```haxe
import flixel.util.FlxSignal;
```

```haxe
// для сигналов без данных используйте FlxSignal
var signal = new FlxSignal();
// для сигналов с данными используйте FlxTypedSignal с корректным типом функции
var stringSignal = new FlxTypedSignal<String->Void>();
```

На заметку: `FlxSignal` это ни что иное, как удобная ссылка на `FlxTypedSignal<Void->Void>`

```haxe
signal.add(voidCallback); // тип должен быть Void->Void
stringSignal.add(stringCallback); // тип должен быть String->Void
```

```haxe
function voidCallback()
{
	trace("Hello");
}
function stringCallback(text:String)
{
	trace(text);
}
```

```haxe
signal.dispatch();
stringSignal.dispatch("World");
```

В вашем сигнале может быть до 4 параметров:
```haxe
var collisionNotify = new FlxTypedSignal<FlxObject->FlxObject->Bool->Bool->Void>();
collisionNotify.add(collisionCallback);

function collisionCallback(source:FlxObject, target:FlxObject, shouldKillSource:Bool, shouldKillTarget:Bool):Void (...)
```

## FlxTimer

```haxe
import flixel.util.FlxTimer;
```

```haxe
// время (в секундах), колбек, кол-во повторов
new FlxTimer().start(10.0, myCallback, 3);
```

```haxe
function myCallback(Timer:FlxTimer):Void
{
}
```
* Установка `loops` в `0` приведет к бесконечному числу повторений.
* `reset(?NewTime)` перезапускает таймер, опционально с новой длительностью.
* `cancel()` останавливает таймер и удаляет его из менеджера таймеров.


## FlxRandom

```haxe
// (Int) от 0 до 10
FlxG.random.int(0, 10);

// (Float) от 0.0 до 10.0
FlxG.random.float(0.0, 10.0);

// (Bool) Шанс в процентах
FlxG.random.bool(50); // 50% шанс, что функция вернет 'true'
FlxG.random.bool(10); // 10% шанс, что функция вернет 'true'
```

## [FlxTween](http://haxeflixel.com/documentation/flxtween/)

[Посмотрите демо](http://haxeflixel.com/demos/FlxTween/) чтобы увидеть визуализацию всех типов `FlxTween`.
* **tween**(Object, Values, Duration, ?Options)

```haxe
import flixel.tweens.FlxTween;
import flixel.tweens.FlxEase;
```

```haxe
// Перемещает спрайт в позицию (100, 200) за 3 секунды
FlxTween.tween(sprite, { x: 100, y: 200 }, 3.0, { ease: FlxEase.quadInOut, complete: myCallback });
```

```haxe
function myCallback(Tween:FlxTween):Void
{
}
```

## FlxTween Options

#### ease
```haxe
{ ease: FlxEase.quadInOut }
```

#### complete
```haxe
{ complete: callbackFunction }
```

```haxe
function callbackFunction(Tween:FlxTween):Void
{
}
```

#### type
```haxe
{ type: FlxTween.PINGPONG }
```
* **FlxTween.BACKWARD:** проигрывает анимацию задом наперед.
* **FlxTween.LOOPING:** после завершения автоматически начинает проигрываться с начала.
* **FlxTween.ONESHOT:** останавливается и удаляет себя из контейнера после завершения анимации.
* **FlxTween.PERSIST:** останавливается при завершении.
* **FlxTween.PINGPONG:** проигрывает анимацию вперед и назад

#### Задержка зацикливания loopDelay
```haxe
{ loopDelay: 1.0 } // 1 секунда
```

#### Задержка начала startDelay
```haxe
{ startDelay: 2.0 } // 2 секунды
```

## FlxEase List

[Посмотрите демо](http://haxeflixel.com/demos/FlxTween/) чтобы увидеть визуализацию всех типов `FlxEase`.

* `backIn`, `backInOut`, `backOut`


* `bounceIn`, `bounceInOut`, `bounceOut`


* `circIn`, `circInOut`, `circOut`


* `cubeIn`, `cubeInOut`, `cubeOut`


* `elasticIn`, `elasticInOut`, `elasticOut`


* `expoIn`, `expoInOut`, `expoOut`


* `quadIn`, `quadInOut`, `quadOut`


* `quartIn`, `quartInOut`, `quartOut`


* `quintIn`, `quintInOut`, `quintOut`


* `sineIn`, `sineInOut`, `sineOut`


## Контейнеры ([FlxGroup](http://haxeflixel.com/documentation/flxgroup))

`FlxGroup` является ссылкой на `FlxTypedGroup<FlxBasic>`. Используйте `FlxTypedGroup<MyOwnClass>` если вам нужен доступ к собственным переменным и функциям когда идет итерация по контейнеру.

### Итерация
```haxe
for (member in myGroup)
{
	member.x += 10;
	member.mySpecificFunction(); // myGroup = FlxTypedGroup<MyOwnClass>
}
```


## Столкновения

```haxe
FlxG.overlap(ObjectOrGroup1, ObjectOrGroup2, myCallback);
```

```haxe
function myCallback(Object1:FlxObject, Object2:FlxObject):Void
{
}
```

Или используйте метод `FlxG.collide()`, который вызывает `FlxG.overlap()` выставляет параметр `ProcessCallback` в значение `FlxObject.separate()`.

### Установка границ игрового мира

```haxe
// столкновения не будут работать за пределами границ
collision won't work outside the bounds, и по умолчанию они имеют размер только одного экрана
FlxG.worldBounds.set(tilemap.x, tilemap.y, tilemap.width, tilemap.height);
```

### Быстрая проверка наличия столкновения

```haxe
// установка флагов соприкосновения
FlxG.collide(player, level);

if (player.isTouching(FlxObject.DOWN))
{
	// игрок стоит на земле и может прыгать
}

// сбросит касание флагов при вызове
super.update(elapsed);
```

### Перемещение спрайта в новую позицию

```haxe
// после установки координат нового положения спрайта
setPosition(10, 100);
// не забудьте обновить переменную 'last' если вы не хотите перекрывать колбеки для объектов между старыми и новыми позициями спрайта
last.set(x, y);
```

### Попиксельная проверка столкновений

```haxe
var overlapping = FlxG.pixelPerfectOverlap(sprite1, sprite2);
```

## Отрисовка форм

**Динамическая отрисовка:** круга, эллипса, линии, многоугольника, треугольника, прямоугольника, прямоугольника со скругленными углами, сложный прямоугольник.

```haxe
using flixel.util.FlxSpriteUtil;
```

Документация Haxe по ключевому слову `using`: [haxe.org/manual/lf-static-extension.html](https://haxe.org/manual/lf-static-extension.html).

```haxe
var canvas = new FlxSprite();
canvas.makeGraphic(FlxG.width, FlxG.height, FlxColor.TRANSPARENT, true);
add(canvas);
```

Последний аргуменит метода `makeGraphic()` - уникальность (`Unique`), определяет должна ли созданная графика быть уникальным экземпляром в графическом кеше, если вы создаете несколько графических объектов, установите для него значение `true`, чтобы избежать конфликтов.

```haxe
var lineStyle:LineStyle = { color: FlxColor.RED, thickness: 1 };
var drawStyle:DrawStyle = { smoothing: true };
```

```haxe
// Круг
canvas.drawCircle(X, Y, Radius, Color, lineStyle, drawStyle);

// Эллипс
canvas.drawEllipse(X, Y, Width, Height, Color, lineStyle, drawStyle);

// Линия
canvas.drawLine(StartX, StartY, EndX, EndY, lineStyle);

// Многоугольник
var vertices = new Array<FlxPoint>();
vertices[0] = new FlxPoint(0, 0);
vertices[1] = new FlxPoint(100, 0);
vertices[2] = new FlxPoint(100, 300);
vertices[3] = new FlxPoint(0, 100);
canvas.drawPolygon(vertices, Color, lineStyle, drawStyle);

// Треугольник
canvas.drawTriangle(X, Y, Height, Color, lineStyle, drawStyle);

// Прямоугольник
canvas.drawRect(X, Y, Width, Height, Color, lineStyle, drawStyle);

// Прямоугольник со скругленными углами
canvas.drawRoundRect(X, Y, Width, Height, EllipseWidth, EllipseHeight, Color, lineStyle, drawStyle);

// Сложный прямоугольник со скругленными углами
canvas.drawRoundRectComplex(X, Y, Width, Height, TopLeftRadius, TopRightRadius, BottomLeftRadius, BottomRightRadius, Color, lineStyle, drawStyle);
```

Используйте `canvas.fill(FlxColor.TRANSPARENT);` чтобы очистить холст.


## HUD

```haxe
// привязывает спрайт к положению камеры
scrollFactor.set(0, 0);
```

### Зумирование в игре, без изменения HUD

```haxe
gameCamera = new FlxCamera(0, 0, screenWidth, screenHeight);
uiCamera = new FlxCamera(0, 0, screenWidth, screenHeight);

gameCamera.bgColor = 0xff626a71;
uiCamera.bgColor = FlxColor.TRANSPARENT;

gameCamera.zoom = 0.5;

FlxG.cameras.reset(gameCamera);
FlxG.cameras.add(uiCamera);

FlxCamera.defaultCameras = [gameCamera];

hudElement.cameras = [uiCamera];
```


## Отладчик

Нажмите клавишу `~` чтобы открыть отладчик в игре, или установите `FlxG.debugger.visible = true` чтобы открыть его с помощью кода.

```haxe
// Вывод в отладчик
FlxG.log.add("My var: " + myVar);
// или
FlxG.log.redirectTraces = true;
trace("My var: ", myVar);

// Наблюдение за переменной
FlxG.watch.add(object, "property");

// Добавление в отслеживание глобальных коорджинат мыши
FlxG.watch.addMouse();

// Создание отдельного теркера для игрока (класса Player), отображение координат "x", "y" и пользовательских полей "jumping" и "ladder"
FlxG.debugger.addTrackerProfile(new TrackerProfile(Player, ["x", "y", "jumping", "ladder"], []));
FlxG.debugger.track(player, "Hero");
```

## Скрытие курсора мыши

```haxe
FlxG.mouse.visible = false;
```

## Добавление гравитации

```haxe
acceleration.y = 600;
```

## Сортировка объектов в FlxGroup

```haxe
// сортировка игровых элементов по Y
group.sort(FlxSort.byY, FlxSort.ASCENDING);

// сортировка с собственной функцией (в примере: по Z)
var group = new FlxTypedGroup<ZSprite>();
group.sort(
	function(order:Int, sprite1:ZSprite, sprite2:ZSprite):Int
	{
		return FlxSort.byValues(order, sprite1.z, sprite2.z);
	},
	FlxSort.ASCENDING
);
```

## Пул FlxPoint

```haxe
// получение из пула FlxPoint
var tileSize = FlxPoint.get(16, 16);

var actionTileset = FlxTileFrames.fromGraphic(FlxG.bitmap.add("assets/images/ui/actions.png"), tileSize);

// убираем обратно в пул для повторного использования
tileSize.put();
```
