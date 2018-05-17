```
title: "FlxSprite"
apiPath: FlxSprite.html
```

```haxe
import flixel.FlxSprite;
```

`FlxSprite` является ключевым во фрейморке Flixel. Он имеет функционал для добавления анимации, движения и другого функицонала, требуемого для большинства игр.

Чаще всего вы захотите унаследоваться от `FlxSprite` для реализации требований вашей конкретной игры. Например класс `SpaceShip` может наследоваться от `FlxSprite` и иметь дополнительные поля, например `shieldStrength` или `shieldPower`. Когда вы наследуете класс от `FlxSprite`, важно помнить о переопределении метода `update` и вызове `super.update()`, как и для любого другого `FlxBasic`.

#### loadGraphic()

Загружает одиночное изображение в `FlxSprite`. Во Flixel используется система хранения ассетов из OpenFL, определяемая настройками xml вашего проекта. Поэтому вам просто необходимо указать путь до требуемого изображения, а компилятор сделает все остальное.

```haxe
var player = new FlxSprite();
player.loadGraphic("assets/player.png");
add(player);
```

#### makeGraphic()

Делает прямоугольную заливку заданным цветом.

```haxe
var whiteSquare = new FlxSprite();
whiteSquare.makeGraphic(200, 200, FlxColor.WHITE);
add(whiteSquare);
```

### Свойство

#### Координаты: x, y
```haxe
whiteSquare.x = 100;
whiteSquare.y = 300;
```

#### Размер: width, height

Автоматически устанавливаются после вызова методов `loadGraphic()` или `makeGraphic()`. Изменение значений самостоятельно влияет только на хитбокс спрайта, но не масштаб. Чтобы изменить размер изображения, используйте `scale`.

```haxe
// get
var getWidth = whiteSquare.width;

// set
whiteSquare.width = 100;
whiteSquare.height = 100;
```

#### Scale
**(FlxPoint)**
Изменяет размер графики в спрайте. *Обратите внимание: хитбокс не изменится автоматически при изменении масштаба. Используйте `updateHitbox()` для обновления хитбокса (или `setGraphicSize()`).*
```haxe
// twice as big
whiteSquare.scale.set(2, 2);

// 50%
whiteSquare.scale.set(0.5, 0.5);
```

#### Offset
**(FlxPoint)**
Контролирует позицию хитбокса у спрайта. Чаще всего требуется установить после изменения высоты спрайта, ширины или масштаба.
```haxe
whiteSquare.offset.set(50, 50);
```

#### Origin
**(FlxPoint)**
Точка вращения. **По умолчанию: center.**

*ВНИМАНИЕ: При изменении origin, отображение и столкновения скорее всего рассинхронизируются после задания поворота.*
```haxe
// задает центр вращения в верхнем левом углу, вместо центра
whiteSquare.origin.set(0, 0);
```

#### ​kill()

Используется для того, чтобы убрать спрайт со сцены, но не удалять его из памяти для возможного повторного использования. Например, если вы хотите вновь создать на карте врага, которого игрок только что убил.

#### destroy()

Это метод используется для полного удаления объекта из памяти. Часто используется в переопределяемом методе destroy класса FlxState.

### Animation

Flixel поддерживает анимацию на спрайтшитах (spritesheet).

![](../images/02_handbook/sprite-animation-example.png)

```haxe
player.loadGraphic("assets/player.png", true, 32, 36);
player.animation.add("walk", [0, 1, 0, 2], 5, true);
player.animation.play("walk");
```
