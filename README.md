# Руководство для начинающих

## 1. шаг 

[GIT](https://git-scm.com/download/win "скачать отсюда")

## 2. шаг

Установить командную строку Git и запустить Git Bash

## Команды

pwd - print currient directory;

cd - change directory;  .. - go to up level: example (cd ..); . - go to currient directory: (cd .);  ls - print directoru stuff iles and othe directories); ls -a - print all (with invizible files and directories);  touch - create new file;  mkdir - create new directory; mkdir -p - create struct of directories: (mkdir -p first/second/third); cp - copy files: (target target place); mv - move files (taget target place); cat print file (only text); rn - remove file; rmdir - remove directory (only empry directory);  rm -r - remove palce with stuff;  more information [Яндекс практикум](https://practicum.yandex.ru)

## 3. шаг

[GitHub](https://github.com)  В правом верхнем углу главной страницы GitHub нажмите на Sign up (англ. «зарегистрироваться»).  На экране будут последовательно появляться поля для ввода.  2.1. Введите адрес электронной почты (англ. Enter your email).  2.2. Придумайте пароль (англ. Create a password).  2.3. Введите имя пользователя (англ. Enter a username).  Платформа спросит, хотите ли вы получать на почту рассылку с обновлениями и новостями (англ. Would you like to receive product updates and announcements via email?).  Введите y, если хотите получать рассылку, или n, если не хотите.  Нажмите кнопку Continue (англ. «продолжить»).  GitHub предложит вам пройти капчу. Сделайте это.   После прохождения капчи нажмите Create account (англ. «создать аккаунт»).  Введите короткий код, который будет отправлен на указанный вами почтовый адрес.

## 4. шаг (Repository) 

Зайдите в свой профиль по ссылке https://github.com/username, где username — имя, которое вы указали при регистрации.  Эта страница — презентация вас и ваших проектов. Её видят другие пользователи. Надпись You don't have any public repositories yet (англ. «у вас пока нет публичных репозиториев») сообщает, что пока у вас нет проектов.  Создайте репозиторий. Для этого перейдите на вкладку Repositories (англ. «репозитории»), а затем нажмите на зелёную кнопку New (англ. «новый») справа.  Открылось окно создания нового репозитория. Назовите его first-project. Название удалённого репозитория необязательно должно совпадать с именем папки проекта у вас на компьютере. Но чтобы не путаться, будем называть их одинаково.  Другие поля вам пока не понадобятся. Смело нажимайте на зелёную кнопку Create repository (англ. «создать репозиторий») внизу.

## 5. шаг (SSH key)

Инструкция по генерации SSH-ключа

Для генерации SSH-пары можно использовать программу ssh-keygen. Откройте терминал и введите следующую команду.

```bash
 ssh-keygen -t ed25519 -C "электронная почта, к которой привязан ваш аккаунт на GitHub" 
```

Используйте электронную почту, к которой привязан ваш GitHub-аккаунт.
    Если вы видите сообщение об ошибке, то, скорее всего, ваша система не поддерживает алгоритм шифрования ed25519. Ничего страшного: используйте другой алгоритм.

```bash 
ssh-keygen -t rsa -b 4096 -C "электронная почта, к которой привязан ваш аккаунт на GitHub"
``` 

После ввода отобразится такое сообщение.

> Generating public/private rsa key pair. // сгенерированы публичный и приватный ключи

Укажите место хранения ключей. Простой вариант — сделать домашний каталог пользователя путём по умолчанию. Для этого нажмите Enter.

macOS

> Enter a file in which to save the key (/Users/you/.ssh/id_rsa): [Press enter]

Windows

> Enter a file in which to save the key (C:\Users\<имя_пользователя>\.ssh\):[Press enter]

Теперь в указанной директории появится пара ключей.  Программа запросит кодовую фразу (англ. passphrase) для доступа к SSH-ключу. Вы можете оставить поле пустым. Для этого нажмите Enter, а затем ещё раз Enter для подтверждения.

> Enter passphrase (empty for no passphrase): [Type a passphrase]
> Enter same passphrase again: [Type passphrase again] 

Готово! Теперь осталось проверить, что ключи действительно сгенерировались. Для этого вызовите эту команду.

```bash
ls -a ~/.ssh
```

На экране должны появиться два файла — один с расширением .pub, другой — без. Файл в .pub — публичный, им можно делиться с веб-сайтами или коллегами. Файл без расширения .pub — приватный. Ни в коем случае не передавайте его никому!

## 6. шаг

Инструкция по связыванию SSH-ключа и GitHub-аккаунта

После выполнения команды ssh-keygen из предыдущего урока в директории ~/.ssh будет создано два файла — id_ed25519 и id_ed25519.pub (или id_rsa и id_rsa.pub — в зависимости от того, какой алгоритм вы использовали):  id_ed25519/id_rsa — приватный ключ (файл без .pub в конце). Ни в коем случае не копируйте его и не делитесь им.  id_ed25519.pub/id_rsa.pub — публичный ключ (на это указывает расширение .pub).  Скопируйте содержимое файла с публичным ключом в буфер обмена.

macOS

скопировать содержимое ключа в буфер обмена:
```bash
pbcopy < ~/.ssh/id_rsa.pub
```
для ed25519:
```bash
pbcopy < ~/.ssh/id_ed25519.pub 
```

Здесь используется команда pbcopy — она копирует поток данных в буфер обмена. Запись pbcopy < ~/.ssh/id_rsa.pub означает: «Скопируй в буфер обмена всё содержимое файла ~/.ssh/id_rsa.pub».
В качестве альтернативы вы можете распечатать файл на экран с помощью cat ~/.ssh/id_rsa.pub и скопировать его вручную.

Windows

скопировать содержимое ключа в буфер обмена:
```bash
 clip < ~/.ssh/id_rsa.pub
```
для ed25519:
```bash
clip < ~/.ssh/id_ed25519.pub
``` 

Если clip не сработает, выведите содержимое файла с помощью

```bash
cat ~/.ssh/id_rsa.pub
```

или

```bash
cat ~/.ssh/id_ed25519.pub
```

и скопируйте вывод в буфер обмена из консоли.

Перейдите на GitHub и выберите пункт Settings (англ. «настройки») в меню аккаунта.  В меню слева нажмите на пункт SSH and GPG keys.  В открывшейся вкладке выберите New SSH key (англ. «новый SSH-ключ»).  В поле Title (англ. «заголовок») напишите название ключа. Например, Personal key (англ. «личный ключ»). В поле Key type (англ. «тип ключа») должно быть Authentication Key (англ. «ключ аутентификации»).  В поле Key скопируйте ваш ключ из буфера обмена.

Нажмите на кнопку Add SSH key (англ. «добавить SSH-ключ»).  Проверьте правильность ключа с помощью следующей команды.
```
bash  ssh -T git@github.com
```

Если это первый раз, когда вы используете Git, чтобы поделиться проектом на GitHub, появится похожее предупреждение.

The authenticity of host 'github.com (140.82.121.4)' can't be established. ED25519 key fingerprint is SHA256:+DiY3wvvV6TuJJhbpZisF/zLDA0zPMSvHdkr4UvCOqU. This key is not known by any other names. Are you sure you want to continue connecting (yes/no/[fingerprint])? 

Это предупреждение сообщает, что вы никогда не соединялись с сервером GitHub. Поэтому Git не может гарантировать, что сервер является тем, за кого он себя выдаёт.
Для подтверждения подлинности сервер генерирует и публикует ключи SHA256. Вы можете проверить ключи GitHub по этой ссылке. Если ключ в предупреждении совпадает с тем, что вы видите на сайте, значит, сервер является действительным. Введите yes, чтобы продолжить. Вы увидите приветствие на экране.

Hi %ВАШ_АККАУНТ%! You've successfully authenticated, but GitHub does not provide shell access.

## 7. шаг

Привязать удалённый репозиторий к локальному — git remote add
Перейдите на страницу удалённого репозитория, выберите тип SSH и скопируйте URL. Кнопка справа позволит сделать это мгновенно.
Откройте консоль, перейдите в каталог локального репозитория и введите команду git remote add (от англ. remote — «удалённый» и add — «добавить»).

```bash  cd ~/dev/first-project  git remote add origin git@github.com:%ИМЯ_АККАУНТА%/first-project.git  ```

Команде необходимо передать два параметра: имя удалённого репозитория и его URL. В качестве имени используйте слово origin. А URL вы скопировали со страницы удалённого репозитория.
💡 Как выполнить вставку в командную строку?
В командную строку нельзя вставить текст из буфера обмена с помощью привычного сочетания Ctrl+V. На Windows (в Git Bash) и Linux для этого используется сочетание Ctrl+Shift+V, а на macOS — Cmd+V.
Также можно нажать правую кнопку мыши и выбрать пункт Paste (англ. «вставить») в выпадающем меню.
origin (англ. «источник») — стандартный псевдоним, с помощью которого можно обращаться к главному удалённому репозиторию (обычно такой репозиторий один). Это значительно упрощает работу.
Убедиться, что репозитории связаны, — git remote -v
Отлично: вы связали локальный репозиторий с удалённым. Осталось убедиться, что всё работает, с помощью следующей команды.

```bash  git remote -v  ```  origin    git@github.com:%ИМЯ_АККАУНТА%/%ИМЯ-ПРОЕКТА%.git (fetch)  origin    git@github.com:%ИМЯ_АККАУНТА%/%ИМЯ-ПРОЕКТА%.git (push) 

В выводе вы должны увидеть две строчки, аналогичные тем, что показаны выше.
Флаг -v — короткая форма флага --verbose (англ. «подробный»). Он позволяет показать больше информации в выводе. 


# Заголовок первого уровня
## Заголовок второго уровня
### Заголовок третьего уровня

## Выделение кода

Чтобы выделить текст как код, поместите его в тройные кавычки `````. 

```
mkdir my_project
cd my_project
git init
```
Это лишь некоторые функции markdown. 