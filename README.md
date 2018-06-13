![](https://raw.github.com/HaxeFlixel/haxeflixel.com/master/src/files/images/flixel-logos/flixel-docs.png)

[flixel](https://github.com/HaxeFlixel/flixel) | [дополнения](https://github.com/HaxeFlixel/flixel-addons) | [ui](https://github.com/HaxeFlixel/flixel-ui) | [демо](https://github.com/HaxeFlixel/flixel-demos) | [инструменты](https://github.com/HaxeFlixel/flixel-tools) | [шаблоны](https://github.com/HaxeFlixel/flixel-templates) | [документация](https://github.com/HaxeFlixel/flixel-docs) | [haxeflixel.com](https://github.com/HaxeFlixel/haxeflixel.com)

## О HaxeFlixel

Это основное место для документации HaxeFlixel. Pull реквесты будут периодически выкладываться на сайт, поэтому, пожалуйста, помогите нам улучшить документацию HaxeFlixel.

## Содержание

* Основная документация доступна в разделе [haxeflixel.com/documentation](http://www.haxeflixel.com/documentation).
* Документация по API.

### Основная документация

Основная документация состоит из файлов `*.html.md` в папке `./documentation`. Каждая директория и файлы начинаются с префикса в виде номера, определяющего порядок на [странице] (https://github.com/HaxeFlixel/haxeflixel.com).

Дополнительные страницы могут быть добавлены, используя то же расширение и используя особый формат заголовков, например:

	```
	title: "Страница документации"
	```
	
	Используйте обычную разметку GitHub для этой страницы.
	`title:` чувствителен к регистру.

Синтаксис разметки, используемый в документах - это [GitHub-Flavored-Markdown](https://help.github.com/articles/github-flavored-markdown), поэтому очень удобно напрямую редактировать файлы через веб-редактор GitHub.

### Документация по API

Документация по API находится в папке `./api`, она сгенерирована с помощью [dox](https://github.com/HaxeFlixel/dox). Вы можете просмотреть документацию в автономном режиме, запустив `nekotools server` в этом каталоге и перейдя по ссылке [localhost:2000](http://localhost:2000/).

Чтобы создавать документы API самостоятельно, необходимо установить dox (инструкции доступны [по ссылке](https://github.com/HaxeFlixel/dox/blob/master/README.md)).

Далее вы можете:

- Перейти в `api/dox-gen`
- Запустить `haxe testdocs.hxml`

или

- Запустить таск сборки "Test Docs" в VSCode

Документы будут сгенерированы в папке `api`.

Обратите внимание, что для этого будут использованы текущие версии библиотек haxelib flixel, например если у вас установлен `haxelib git flixel` в `dev` ветке и т.д.
