```
title: "Часто задаваемые вопросы"
```

#### Необходимо ли мне сначала выучить Flixel (AS3) до HaxeFlixel?
Нет, возможно сразу перейти к изучению HaxeFlixel, хотя если у вас есть опыт с AS3, это вам поможет. 

#### Необходимо ли мне изучить ActionScript до Haxe?
Нет, хотя такой опыт вам не помешает.

#### Необходимо ли мне изучить OpenFL чтобы использовать HaxeFlixel?
Нет, HaxeFlixel полностью перекрывает его.

#### Где я могу найти еще туториалы?

- [@SeiferTim's](https://twitter.com/SeiferTim) [Dungeon Crawler туториал](http://haxeflixel.com/documentation/tutorials/)

- [atomicptr's](https://github.com/atomicptr/GameMechanicExplorer-HaxeFlixel) [Game Mechanic Explorer порт](http://gme.qr9.de/)

- [Видео от Christopher Butler](https://www.youtube.com/watch?v=LpKvSPwHOP8&list=PLi0ypjD5PcV9xdjycW0hYi_HD297012tE)
(охватывает все: от установки, до прототипирования платформера).

#### Я нашел ошибку, куда я могу сообщить?
В [официальный репозиторий GitHub](https://github.com/HaxeFlixel/flixel/issues).

#### Будут ли поддерживаться новые консоли?
В конце концов - да! Почитайте об этом побольше [тут](https://groups.google.com/d/topic/haxeflixel/NUOpgGUKMvE/discussion).

#### Мои звуки прерываются!?
На некоторых платформах можно попробовать вручную кешировать звуки `FlxG.sound.cache("sound");` or `FlxG.sound.cacheAll();` чтобы кешировать все сразу.

#### Мой игрок падает за экран после прохождения некоторого расстояния!
Столкновения ограничены областью, заданной в `FlxG.worldBounds`. Например, в платформерах, где эта область должна быть больше, вам необходимо настроить ее вручную.

#### Могу я делать 3D игры на HaxeFlixel?
Нет, фреймворк ограничен только 2D графикой.

#### Как я могу защитить свои ассеты от кражи?
Если вы добавите `embed="true"` в тег `<assets path="assets">` файла `Project.xml`, ассеты будут вшиты в `.exe`.
