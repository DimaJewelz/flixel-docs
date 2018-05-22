```
title: "iOS"
```

<img src="/images/targets/ios-logo.png" width="160px" style="float:left; padding:10px" />

Таргет iOS использует несколько фреймворков для компиляции в нативный код под iOS из вашего кода на Haxe. OpenFL использует [Hxcpp](http://lib.haxe.org/p/hxcpp) и XCode, поэтому виртуальная машина не используется.
Когда вы компилируете проект под iOS, то файл с проектом под XCode создается автоматически, поэтому вы можете использовать профайлер и набор инструментов самого XCode.

Компилятор Haxe использует ```cpp``` таргет, чтобы скомпилировать ваш ```Haxe``` код для библиотеки OpenGL [LibSDL](http://libsdl.org).
iOS является частью группы таргетов под cpp. Поэтому когда разработчики упоминают ```cpp```, эта тема может иметь отношение к HaxeFlixel iOS.

Благодаря использованию [OpenFL](http://openfl.org) и OpenGL с [LibSDL](http://libsdl.org), способы отображения отличаются от первоначальных с использованием Flash.
iOS использует т.н. `Texture Batching` в графическом ускорителе для лучшей производительности на мобильных устройствах.

### Условные выражения
----

```
#if cpp
//код для iOS
#end

#if ios
//код для iOS
#end

#if mobile
//код для iOS
#end
```

### Настройки XML файла проекта

Mobile таргеты могут использовать значение ширины и высоты окна равным 0. Это специальное значение, которое означает полноэкранное отображение.

```
<window width="0" height="0" background="#FFFFFF" fps="60" />
```

OpenFL также предоставляет следующие специальные настройки для desktop таргетов:

```
<window hardware="true" allow-shaders="true" require-shaders="true" if="cpp"/>
<window vsync="true" antialiasing="4" if="cpp" />
<window orientation="portrait" /> || <window orientation="landscape" if="cpp"/>
```

PNG иконки приложения: (для более подробной информации посмотрите статью [рекомендации для создания иконок для iOS](https://developer.apple.com/library/ios/documentation/userexperience/conceptual/mobilehig/IconMatrix.html))

```
<set name="PRERENDERED_ICON" value="true" />

<icon path="Icon.png" size="57" if="ios" />
<icon path="Icon@2x.png" size="114" if="ios" />
<icon path="Icon-72.png" size="72" if="ios" />
<icon path="Icon-72@2x.png" size="144" if="ios" />

<launchImage path="Default.png" width="320" height="480" if="ios" />
<launchImage path="Default@2x.png" width="640" height="960" />
<launchImage path="Default-Portrait~ipad.png" width="768" height="1024" if="ios" />
<launchImage path="Default-Portrait@2x~ipad.png" width="1536" height="2048" if="ios" />
<launchImage path="Default-Landscape~ipad.png" width="1024" height="768" if="ios" />
<launchImage path="Default-Landscape@2x~ipad.png" width="2048" height="1536" if="ios" />
<launchImage path="Default-568h@2x.png" width="640" height="1136" if="ios" />
```

### Команды компиляции

Редакторы Sublime Text, Flash Develop и IntelliJ IDEA поддерживают компилирование под iOS через интерфейс.

#### Командная строка

Базовая команда для компилирования и тестирования под iOS:

```
lime test ios
```

Запустите эту команду в корневой папке вашего проекта, по умолчанию будет использован файл настроек project.xml.

Если вы хотите использовать iOS симулятор, добавьте `-simulator` в команду запуска/тестирования.

```
lime test ios -simulator
```
