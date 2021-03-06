```
title: "Отладчик - взаимодействие с игровыми объектами"
```

Инструмент "Взаимодействие" (доступен по кнопке ![](../images/02_handbook/debugger/icons/interactive.png) в отладчике) позволяет вам изменять игровые элементы, например двигать спрайты прямо во время выполнения игры.

Однако рекомендуется ставить игру на паузу ![](../images/02_handbook/debugger/icons/pause.png) перед использованием этого инструмента. Вы всегда можете снять игру с паузы, нажав кнопку "Play" ![](../images/02_handbook/debugger/icons/arrowRight.png), после того, как вы закончили управление игровыми элементами. Если игра не приостановлена во время взаимодействия, объекты, которые движутся с ускорением, будут продолжать двигаться, что затруднит работу.

## Инструменты взаимодействия

Когда взаимодействие включено, в панели отображаются несколько инструментов в левой части экрана. Ниже описание каждого из этих инструментов.

### Указатель

Указатель ![](../images/02_handbook/debugger/icons/cursorCross.png) позволяет вам выбрать игровые элементы. Чтобы использовать его, просто кликните на элементы на экране:

![](../images/02_handbook/debugger/interaction-pointer-simple-select.gif)

На данный момент можно выбрать только элементы, которые расширяют `FlxSprite` (что исключает выбор тайлов). Выбранные элементы подсвечиваются красным. Чтобы снять выделение - кликните по пустому месту.

Вы можете удалять/добавлять элементы к уже выбранным удерживая `CTRL` при клике. Также можно удалять/добавлять несколько элементов одновременно, если кликнуть и провести курсором для выбора области:

![](../images/02_handbook/debugger/interaction-pointer-fine-picking.gif)

Если нажать кнопку `DELETE`, для всех выбранных элементов отладчик вызовет метод `kill()`. Также можно удерживать клавишу `SHIFT` при нажатии `DELETE`, чтобы вызвать метод `kill()` и удалить элементы из памяти, то есть элементы будут удалены из списка отображения Flixel.

### Перемещение

Инструмент "Перемещение" ![](../images/02_handbook/debugger/icons/mover.png) позволяет вам передвигать игровые объекты, которые были выделены инструментом "Указатель". Чтобы использовать этот функционал, выберите любой элемент (или несколько элементов), используя инструмент указателя, затем выберите инструмент перемещения и перетащите *в любое место* на экране:

![](../images/02_handbook/debugger/interaction-mover.gif)

Выбранные элементы будут следовать за курсором мыши, пока вы не отпустите кнопку мыши.

Инструмент перемещения также активируется, пока нажата клавиша `SHIFT`. Поэтому вы можете перемещать выбранные элементы в любое время, даже когда активен любой другой инструмент. После выбора, удерживайте `SHIFT`, затем перемещайте выбранные элементы:

![](../images/02_handbook/debugger/interaction-mover-shortcut.gif)

Когда вы отпустите `SHIFT`, элементы перестанут перемещаться, и предыдущий инструмент снова станет активным.
