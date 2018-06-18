```
title: "Visual Studio Code"
```

[![](../images/00_getting_started/vscode/vscode-plus-extensions.png)](https://marketplace.visualstudio.com/items?itemName=vshaxe.haxe-extension-pack)

[Visual Studio Code](https://code.visualstudio.com/) это кроссплатформенный редактор кода от Microsoft с открытым кодом. [Расширение для Haxe](https://marketplace.visualstudio.com/items?itemName=nadako.vshaxe) интегрируется в [IDE сервисы компилятора](https://haxe.org/manual/cr-completion.html) и используется для:

- Автодополнения кода
- Перехода к определению 
- Перехода к символу
- Поиска использований
- Поиска неиспользованных импортов
- и др.

Вы можете найти подробную документацию для расширения Haxe в [Wiki](https://github.com/vshaxe/vshaxe/wiki). Текущая страница нацелена на детали, специфичные для Flixel.

### Установка

- Скачайте и установите последнюю версию [Visual Studio Code](https://code.visualstudio.com/).
- Перейдите во вкладку Расширений и установите [расширение Lime](https://marketplace.visualstudio.com/items?itemName=openfl.lime-vscode-extension). Это также установит расширения для Haxe.

    ![](../images/00_getting_started/vscode/lime-installation.png)

### Конфигурация проекта

VSCode хранит настройки проекта в подпапке `.vscode` - [flixel-tools](http://haxeflixel.com/documentation/flixel-tools/) может создать такие настройки для проектов на Flixel. Для этого укажите VSCode в качестве основного редактора во время выполнения команды `setup` или добавьте `-ide vscode` в команду, которую вы запускаете.

**Обратите внимание:** убедитесь, что у вас установлены последние версии flixel-tools и flixel-templates:

```
haxelib update flixel-tools
haxelib update flixel-templates
```

Существует несколько опций для создания проекта с конфигурацией `.vscode`:

1. Создание нового, пустого проекта:

    ```
    flixel template -n "VSCodeTest" -ide vscode
    ```

2. Создание нового проекта на основе одного из [демо проектов](/demos):

    ```
    flixel create -ide vscode
    ```

3. Добавление папки `.vscode` в уже существующий проект, например текущий рабочий каталог:

    ```
    flixel configure . -ide vscode
    ```

4. Добавление файлов конфигурации VSCode в весь каталог проектов, таких как flixel-demos:

    ```
    flixel configure C:\HaxeToolkit\haxe\lib\flixel-demos\git -ide vscode
    ```

### Автодополнение кода

После установки расширения Lime и создания проекта с папкой `.vscode`, откройте проект в редакторе `File` -> `Open Folder`. Если директория определяется как Lime-проект (должен присутствовать файл `Project.xml`), вы увидите выпадающие меню в строке состояния:

![](../images/00_getting_started/vscode/lime-dropdowns.png)

Функция автодополнения кода теперь должна работать:

![](../images/00_getting_started/vscode/completion.png)

Если возникли сложности, обратитесь к статье [поиск неисправностей в расширении Haxe](https://github.com/vshaxe/vshaxe/wiki/Troubleshooting).

### Сборка

Сборка и запуск ваших проектов в VSCode сделана с помощью _задач_. Вы можете посмотреть список доступных задач через `Tasks` -> `Run Task...`:

![](../images/00_getting_started/vscode/tasks.png)

Чтобы скомпилировать и запустить ваш проект, выберите задачу `lime: test`. С шаблоном Flixel этот таск стоит по умолчанию для компиляции, поэтому вы можете также вызвать его непосредственно через `Tasks` -> `Run Build Task...` или нажатием `Ctrl+Shift+B`:

![](../images/00_getting_started/vscode/run-build-task.png)

Вы можете назначить горячую клавишу, чтобы запустить таск `Run Task...` или поменять горячие клавиши для `Run Build Task...` на что-то более удобное, например `F5`. Вы можете сделать это в `File` -> `Preferences` -> `Keyboard Shortcuts`.

Наконец, вы можете изменить таргет и конфигурацию билда (Debug, Release, Final) с помощью выпадающего меню в строке состояния:

![](../images/00_getting_started/vscode/change-config.gif)


### Ошибки компилятора / Окно ошибок

По умочанию ошибки компилятора и предупреждения отображаются в окне _Terminal_ внизу экрана. Вы можете перейти к источнику ошибки через комбинацию клавиш `Ctrl`+`Click` на пути файла:

![](../images/00_getting_started/vscode/terminal.png)

Также вы можете переключиться на вкладку _Problems_, которая имеет более удобное оформление. Оно показывает ошибки / предупреждения из компиляции, а также диагностику, которая обновляется каждый раз при сохранении файла.

![](../images/00_getting_started/vscode/problems.png)

### Отладка во Flash

Шаблон `.vscode` из flixel-tools уже включает `launch.json`, требуемый для отладки во Flash. Чтобы использовать отладчик, вам также необходимо установить расширение [Flash Debugger](https://marketplace.visualstudio.com/items?itemName=vshaxe.haxe-debug). Убедитесь, что:

1. Java установлен и доступен.
2. Плеер "Flash Player projector content debugger" ассоциирован с файлами `.swf`.

Ознакомьтесь с разделом использования в [Readme](https://github.com/vshaxe/flash-debugger#usage) для детальных инструкций.

После этого вам просто нужно выбрать одну из конфигураций запуска, чтобы начать отладку:

![](../images/00_getting_started/vscode/launch-configs.png)

Вот как это должно выглядеть, когда вы нажимаете breakpoint:

<img src="../images/00_getting_started/vscode/flash-debugging.png" style="width:100%;" />

### Отладка HTML5 

По умолчанию файл `launch.json` имеет конфигурацию запуска для отладки HTML5 в Chrome. Это требует установленного расширения [отладчика в Chrome](https://marketplace.visualstudio.com/items?itemName=msjsdiag.debugger-for-chrome). Аналогичные расширения есть и для других браузеров (например [Firefox](https://marketplace.visualstudio.com/items?itemName=hbenl.vscode-firefox-debug)), конфигурация запуска для них примерно одинаковая.

Чтобы начать отладку, выполните эти шаги:

- Выберите `HTML5` и `Debug` в строке состояния:

  ![](../images/00_getting_started/vscode/html5-debug.png)

- Запустите задачу `lime test`(см раздел "Сборка" выше).

- Перейдите в меню отладки, выберите конфигурацию HTML5 и запустите ее:

  ![](../images/00_getting_started/vscode/launch-configs-html5.png)

<img src="../images/00_getting_started/vscode/html5-debugging.png" style="width:100%;" />
