```
title: "Android"
```

<img src="/images/targets/android-logo.svg" width="160px" style="float:left; padding:10px" />

Таргет Android использует несколько фреймворков для компиляции в нативный код под Android из вашего кода на Haxe. OpenFL использует [Hxcpp](http://lib.haxe.org/p/hxcpp) и [Android NDK](http://developer.android.com/tools/sdk/ndk/index.html), поэтому виртуальная машина не используется.

Для настройки таргета под Android, введите команду `lime setup android` после установки HaxeFlixel. Вы можете скачать необходимые компоненты (такие как Android SDK и NDK) или использовать существующие.

Компилятор Haxe использует ```cpp``` таргет, чтобы скомпилировать ваш ```Haxe``` код для библиотеки OpenGL [LibSDL](http://libsdl.org) таким образом, чтобы Android NDK затем мог использовать этот нативный код для вашей игры на Android. Более подробно можно ознакомиться с Android NDK [здесь](http://developer.android.com/tools/sdk/ndk/index.html). Однако этот процесс полностью автоматизирован с помощью [OpenFL](http://openfl.org). Android является частью группы таргетов под cpp. Поэтому когда разработчики упоминают ```cpp```, эта тема может иметь отношение к HaxeFlixel Android.

Благодаря использованию [OpenFL](http://openfl.org) и OpenGL с [LibSDL](http://libsdl.org), способы отображения отличаются от первоначальных с использованием Flash. Android использует т.н. `Texture Batching` в графическом ускорителе для лучшей производительности на мобильных устройствах.

### Условные выражения

```
#if cpp
//код для android
#end

#if android
//код для android
#end

#if mobile
//код для android
#end
```

### Настройки XML файла проекта

Mobile таргеты могут использовать значение ширины и высоты окна равным 0. Это специальное значение, которое означает полноэкранное отображение.

```
<window width="0" height="0" background="#FFFFFF" fps="60" />
```

OpenFL также предоставляет следующие специальные настройки для desktop таргетов:

```
<android target-sdk-version="17" />
<window hardware="true" allow-shaders="true" require-shaders="true" if="cpp"/>
<window vsync="true" antialiasing="4" if="cpp" />
<window orientation="portrait" /> || <window orientation="landscape" if="cpp"/>
```

PNG иконки приложения: (для более подробной информации посмотрите статью [дизайн иконок](http://developer.android.com/design/style/iconography.html))

```
<icon path="36.png" size="36" if="android" />
<icon path="48.png" size="48" if="android" />
<icon path="72.png" size="72" if="android" />
<icon path="96.png" size="96" if="android" />
```

### Команды компиляции

Редакторы Sublime Text, Flash Develop и IntelliJ IDEA поддерживают компилирование под Android через интерфейс.

#### Командная строка

Базовая команда для компилирования и тестирования под Android:

```
lime test android
```

Запустите эту команду в корневой папке вашего проекта, по умолчанию будет использован файл настроек project.xml. Для запуска и тестировния на устройстве оно должно быть подключено с рабочим ADB.

Если вы хотите использовать Android симулятор, добавьте `-simulator` в команду запуска/тестирования. Убедитесь, что API виртуального устройства выше 14 и включено GPU.

```
lime test android -simulator
```
