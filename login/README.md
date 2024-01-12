# Login module

Это модуль для авторизации в vk и Telegram.
Он сохраняет на диске файлы сессий, которые будут использованы другими модулями для связи с серверами vk и Telegram.

## Авторизация в vk

Для авторизации в vk выполните:

```bash
$ ./main.py login vk
```

По умолчанию Приложение предложит вам перейти по ссылке для получения
[ключа доступа](https://dev.vk.com/ru/api/access-token/getting-started).
Этот способ авторизации удобен, если вы уже вошли в vk через браузер и не хотите вводить логин и пароль в Приложении.

Перейдя по ссылке, вы перенаправитесь на страницу с предостережением:
> Пожалуйста, не копируйте данные из адресной строки для сторонних сайтов.
> Таким образом Вы можете потерять доступ к Вашему аккаунту,

Данное сообщение написано потому, что в URL в адресной строке содержится ключ доступа. Именно он необходим Приложению,
поэтому оно попросит вставить этот URL в консоль.

Авторизация завершится, и в консоль выведется `Success!`. Ключ доступа будет сохранён в текущей директории в файл
`vk.session`. 

**Ключ доступа истечёт через 24 часа**, поэтому при необходимости через сутки нужно будет пройти
авторизацию в vk заново.

### Дополнительные опции

```
--with-login       Использовать для авторизации логин и пароль, а не вводить ключ доступа
--show-password    Не скрывать символы вводимого пароля. Имеет эффект только в комбинации с --with-login 
```

## Авторизация в Telegram

Для авторизации в Telegram, выполните:

```bash
$ ./main.py login tg
```

Приложение запросит номер телефона, SMS-код и при необходимости код двухфакторной аутентификации &mdash; 
см. [документацию](https://docs.pyrogram.org/start/auth#user-authorization) Pyrogram.

Авторизация завершится, и в консоль выведется `Success!`. Сессия Telegram будет сохранена в текущей директории в
файле `tg.session`.

В отличие от ключа доступа vk, **сессия Telegram не истекает**, и повторная авторизация не требуется.

### Дополнительные опции

```
--show-password    Не скрывать символы вводимого пароля 
```
 