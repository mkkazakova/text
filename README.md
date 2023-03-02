# lab02

```
$ sudo apt install git
```

Устанвливаем имя пользователя и email

```
$ git config --global user.name "Masha"
$ git config --global user.email "mkkazakova@yandex.ru"
```

В гитхабе создаем свой токен

## I Часть

### Создайте пустой репозиторий на сервисе github.com

Открыть GitHub. Заходим в профиль. Справа сверху "+", New repository

![image](https://user-images.githubusercontent.com/125077130/222095470-e20e284e-1075-485e-a1b3-2e316bf1035a.png)

Нажимаем и настраиваем свой репозиторий. Обязательно оставляем его открытым и не ставим галочку в пункте "Add a README file"


### Создание первого коммита
Переходим в командную строку linux
Создаём директорию. Затем миняем директорию.

```
$ mkdir lab-02 
$ cd ~/lab-02
```

Далее действуем по инструкции, которая дана после создания репозитория:

```
$ echo "# lab02" >> README.md
$ git config --global init.defaultBranch master
$ git init
$ git add README.md
$ git commit -m "first commit"
$ git branch -M master 
$ git remote add origin https://github.com/mkkazakova/lab02.git
$ git push -u origin master 
```

Далее требуется ввести логин (своё имя на GitHub), затем пароль (свой токен)

>git commit – сохранить изменения в репозиторий

>commit -m – ваш комментарий

>git init – создать репозиторий
>git add – добавить файл или папку в репозиторий git

>git branch – управление ветками проекта

>git remote – 

>git push – отправить изменения в удаленный репозиторий

>git remote add origin – добавить удаленный репозиторий

### Создать файл hello_world.cpp в локальной копии репозитория. Реализовать программу Hello world на языке C++ используя плохой стиль кода.

Создаём файл hello_world.cpp:

```
$ nano hello_world.cpp
```
>nano – это консольный текстовый редактор

Пишем в файле:

```
include <iostream>

using namespace std;

int main() 
{
    cout << "Hello World!";
    return 0;
}
```
ctrl+O  enter

Для проверки можно использовать (выводит текст файла на консоль):

```  
$ cat hello_world.cpp
```
  
### Добавить этот файл в локальную копию репозитория

```
$ git add hello_world.cpp
```

### Закоммитьте изменения с осмысленным сообщением

Сообщение: "cpp file created"

```
$ git commit -m "cpp file created"
```

### Изменитьте исходный код так, чтобы программа через стандартный поток ввода запрашивалось имя пользователя. А в стандартный поток вывода печаталось сообщение Hello world from @name, где @name имя пользователя.

Скачиваем пакет, который позволяет использовать edit
```
$ sudo snap install sublime-text --classic
$ alias edit=subl
```
Редактируем файл:
```
$ edit "hello_world.cpp"
```

Пишем в файле:

```
include <iostream>
include <string>

using namespace std;

int main() 
{
    string str;
    getline(cin, str);
    cout << "Hello World from " << str;
    return 0;
}
```

### Закоммитьте новую версию программы

```
$ git commit -am "cpp file changed"
```

Мы не используем $ git add, т.к. файл был добавлен ранее

### Запуште изменения в удалёный репозиторий

```
$ git push -u origin master
```
>git push – отправить изменения в удаленный репозиторий

Далее требуется ввести логин (своё имя на GitHub), затем пароль (свой токен)

### Проверьте, что история коммитов доступна в удалёный репозитории

На сайте github нужно зайти в lab02. Нажать на commit. Будет видна история изменений.


## II Часть

### В локальной копии репозитория создайте локальную ветку patch1

Создадим ветку:

```
$ git checkout -b patch1
```
>git checkout – переключение между ветками
>-b – который действует как вспомогательный метод, позволяя создать новую ветку и сразу переключиться на нее

### Внесите изменения в ветке patch1 по исправлению кода и избавления от using namespace std;

Редактируем файл:

```
$ edit "hello_world.cpp" 
```

Убираем "using namespace std;" и добисываем "std::":
```
include <iostream>
include <string>

int main() 
{
    string str;
    getline(std::cin, str);
    std::cout << "Hello World from " << str;
    return 0;
}
```

### commit, push локальную ветку в удалённый репозиторий

```
$ git commit -am "delete using namespace std;"
$ git push -u origin patch1
```

Далее требуется ввести логин (своё имя на GitHub), затем пароль (свой токен)

>-a – эта команда включает только изменения отслеживаемых файлов (тех, которые были в какой-то момент добавлены в историю с помощью команды git add)

>-m – создает коммит с указанным комментарием

>-a и -m – эта комбинация параметров создает коммит всех проиндексированных изменений и добавляет к коммиту подставленный комментарий

>git push – отправить изменения в удаленный репозиторий. -u добавляет отслеживающую ссылку на вышестоящий сервер, на который вы отправляете данные

### Проверьте, что ветка patch1 доступна в удалёный репозитории.
    
Заходим в GitHub
Заходим в свой репозиторий
Там будет написано, что patch1 доступна

### Создайте pull-request patch1 -> master
    
В оранжевом окошке жмем зеленую кнопку "compare & pull-request"
Жмём зеленую кнопку: создать

### В локальной копии в ветке patch1 добавьте в исходный код комментарии

Редактируем файл:

```
$ edit "hello_world.cpp" 
```

Добавляем комментарии:

```
include <iostream>
include <string>

int main() 
{
    string str; // name
    getline(std::cin, str); // read name
    std::cout << "Hello World from " << str;
    return 0;
}
```

### commit, push

Закоммитем и запушим:

```
$ git commit -am "Code with comments"
$ git push -u origin patch1
```

Далее требуется ввести логин (своё имя на GitHub), затем пароль (свой токен)

>git push – отправить изменения в удаленный репозиторий

### Проверьте, что новые изменения есть pull-request
    
Зайти на GitHub. Нажать на lab02. Найти ветки, выбрав вкладку "Pull request". Там будет большая зелёная надпись "delete using namespace std;". Нажимаем и видим несколько изменений.

### В удалённый репозитории выполните слияние PR patch1 -> master и удалите ветку patch1 в удаленном репозитории.
    
Зелёная кнопка "Merge". Нажимаем. Нажимаем второй раз (подтверждаем). Возвращаемя в "Pull request". Нажимаем на "delete using namespace std;". Удаляем ветку.

### Локально выполните pull

Отправляем изменения из удаленного репозитория в локальный:
```
$ git pull origin 
```
Будет надпись "Already up to date"


### С помощью команды git log просмотрите историю в локальной версии ветки master

Смотрим полную историю, затем отдельно историю ветки master:

```
$ git log 
$ git log master
```

### Удалите локальную ветку patch1

Создаём новую ветку origin. Переключаемся на неё. Затем удаляем ветку patch1

```
$ git checkout -b origin
$ git branch -d patch1 
```


## III Часть

### Создать новую локальную ветку patch2

Создаём и переключаемся на ветку patch2. Удаляем ветку origin
```
$ git checkout -b patch2
$ git branch -d origin
```

### Измените code style с помощью утилиты clang-format. Например, используя опцию -style=Mozilla

Устанавливаем clang-format
```
$ sudo apt install clang-format
$ clang-format -i -style=Mozilla "hello_world.cpp"
```
**Консоль не должна ничего дать в ответ

>clang-format – это инструмент для автоматического форматирования кода на C/C++

>-i – опция, форматирующая файлы

### commit, push, создайте pull-request patch2 -> master

```
$ git commit -am "Changed code style in cpp file"
$ git push -u origin patch2
```

Далее требуется ввести логин (своё имя на GitHub), затем пароль (свой токен)

В профиле GitHub в оранжевом окошке жмем зеленую кнопочку "compare & pull-request"
Жмём зеленую кнопку: создать


### В ветке master в удаленном репозитории измените комментарии, например, расставьте знаки препинания, переведите комментарии на другой язык.

Переключаемся на ветку master

```
$ git checkout master
```

Будет написано, что ветка отстала

Открываем файл

```
$ edit "hello_world.cpp"
```

Меняем комментарии:

```
include <iostream>
include <string>

int main() 
{
    string str; // имя :-(
    getline(std::cin, str); // читаем имя (-_-)
    std::cout << "Hello World from " << str;
    return 0;
}
```

Коммитим и пушим в patch2
```
$ git commit -am "Fixed coment"
$ git push -u origin master
```

Далее требуется ввести логин (своё имя на GitHub), затем пароль (свой токен)


### Убедитесь, что в pull-request появились конфликтны

Зайти на GitHub. Нажать на lab02. Найти ветки, выбрав вкладку "Pull request". Будет надпись о конфликте.

### Исправьте конфликты

```
$ git pull origin master
$ git rebase master
```

Пишет, что ветка master обновлена

>pull – интегрировать удаленный репозиторий origin с локальным master

>rebase – процесс перемещения или объединения последовательности коммитов в новый базовый коммит

Чуть-чуть меняем код:

```
include <iostream>
include <string>

int main() 
{
    string str; // имя :-(
    getline(std::cin, str); // читаем имя (-_-)
    std::cout << "Hello World from " << str;
    std::cout << endl;
    return 0;
}
```

Закоммитим

```
$ edit "hello_world.cpp"
$ git commit -am "Update code"
```

### Сделайте force push в ветку patch2

Меняем ветку на patch2. Объединяем с веткой master
```
$ git checkout patch2
$ git merge master
```

Выводит конфликт:

```
Auto-merging hello_world.cpp
CONFLICT (content): Merge conflict in hello_world.cpp
Automatic merge failed; fix conflicts and then commit the result.
```

Добавляем файлю Коммитим.
```
$ git add "hello_world.cpp"
$ git commit -am "Last fix"
$ git push -f origin patch2
```

Далее требуется ввести логин (своё имя на GitHub), затем пароль (свой токен)

Следует надпись о том, что всё обновлено

>push -f – принудительная перезапись

### Убедитель, что в pull-request пропали конфликтны

Зайти на GitHub. Нажать на lab02. Найти ветки, выбрав вкладку "Pull request".
Будет видно, что конфликтов нет

### Вмержите pull-request patch2 -> master

Зелёная кнопка "Merge". Нажимаем. Нажимаем второй раз (подтверждаем).


