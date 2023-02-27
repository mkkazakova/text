I Часть

$ sudo apt install git
$ man git - проверка
**Устанвливаем имя пользователя и email
$ git config --global user.name "Masha"
$ git config --global user.email "mkkazakova@yandex.ru"
**Делаем данную процедуру на будущее


	Пункт 1:
Открываем GitHub - Заходим в профиль и там видим "Repositories" - Кликаем и переходим во вкладку с репозиториями
Там можно увидеть зеленую кнопочку "New" - Нажимаем и настраиваем свой репозиторий
**Обязательно оставляем его открытым и НЕ СТАВИМ ГАЛОЧКУ в пункте "Add a README file"


	Пункт 2:
$ mkdir lab-02 - Создаём директорию
$ cd ~/lab-02 - Меняем директорию

Из инструкции с сайта:

$ echo "# lab02" >> README.md
git config --global init.defaultBranch master (сами добавили)
git init
git add README.md
git commit -m "first commit"
git branch -M master (изменила main на master)
git remote add origin https://github.com/mkkazakova/lab02.git
git push -u origin master (изменила main на master)

**Потребует ввести логин - вводишь своё имя на GitHub
**Потребует ввести пароль - вводишь свой токен, который ты создала ранее
Логин, пароль:
mkkazakova
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


	Пункт 3:
$ nano hello_world.cpp

Пишем в файле:
-----------------------------------
include <iostream>

using namespace std;

int main() 
{
    cout << "Hello World!";
    return 0;
}
-----------------------------------
ctrl+O 
enter

$ cat hello_world.cpp


	Пункт 4:
$ git add hello_world.cpp


	Пункт 5:
$ git commit -m "cpp file created"


	Пункт 6:
$ sudo snap install sublime-text --classic
$ alias edit=subl

$ edit "hello_world.cpp"
**Откроется окно, где нужно исправить код
-----------------------------------
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
-----------------------------------


	Пункт 7:
$ git commit -am "cpp file changed"
**Мы не используем $ git add, так как файл уже был добавлен в "Пункте 4"


	Пункт 8:
$ git push -u origin master

Логин, пароль:
mkkazakova
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



II Часть

	Пункт 1:
Создадим ветвь для разработки:
$ git checkout -b patch1


	Пункт 2:
$ edit "hello_world.cpp" - для исправления
-----------------------------------
include <iostream>
include <string>

int main() 
{
    string str;
    getline(std::cin, str);
    std::cout << "Hello World from " << str;
    return 0;
}
-----------------------------------
$ cat "hello_world.cpp" - проверка (выводит на консоль прогу)


	Пункт 3:
$ git commit -am "delete using namespace std;"
$ git push -u origin patch1

Логин, пароль:
mkkazakova
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


	Пункт 4:
Заходим в GitHub
Заходим в свои репозитории
Там будет оранжевое окошко, которое свидетельствует, что patch1 доступна


	Пункт 5:
В оранжевом окошке жмем зеленую кнопочку "...& pull-request"
** Появится окно для комментария, последний не обязателен.
** Просто жмём зеленую кнопку: создать


	Пункт 6:
$ edit "hello_world.cpp" - для добавления коментариев
-----------------------------------
include <iostream>
include <string>

int main() 
{
    string str; // name
    getline(std::cin, str); // read name
    std::cout << "Hello World from " << str;
    return 0;
}
-----------------------------------
$ cat "hello_world.cpp" - проверка (выводит на консоль прогу)


	Пункт 7:
$ git commit -am "Code with comments"
$ git push -u origin patch1

Логин, пароль:
mkkazakova
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


	Пункт 8:
Зайти на GitHub 
Нажать на lab02. 
Найти ветки, выбрав вкладочку "Pull request"
Там будет большая зелёная надпись "delete using namespace std;" 
Кликаем по ней и видим несколько изменений


	Пункт 9:
Большая зелёная кнопка "Merge"
Кликаем по ней, а затем еще раз (поддтверждаем)
** После данного действия пропадет единичка на вкладе "Pull request"
** После этого все изменения применятся сразу во вкладке "Code"

Возвращаемя в "Pull request"
Рядом с фиолетовым значком будет "Fixed cpp file", выбираем его
Жмем на синюю "Clear current search query, filters, and sorts"
** Всё пропадёт, но так и должно быть


	Пункт 10:
$ git pull origin - чтобы посмотреть

**Если нет надписи: "Already up to date", то 
$ git checkout master
$ git pull origin


	Пункт 11:
$ git log - отображает полною историю
$ git log master


	Пункт 12:
$ git checkout -b origin (создали НОВУЮ ветку origin и переключились на неё)
$ git branch -d patch1  (дабы была возможноть удалить patch1) 



 III Часть

        Пункт 1:
$ git checkout -b patch2
$ git branch -d origin


	Пункт 2:
$ sudo apt install clang-format
$ clang-format -i -style=Mozilla "hello_world.cpp"
**Консоль не должна ничего дать в ответ


	Пункт 3:
$ git commit -am "Changed code style in cpp file"
$ git push -u origin patch2

Логин, пароль:
mkkazakova
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

В профиле GitHub в оранжевом окошке жмем зеленую кнопочку "...& pull-request"
**Появится окно для комментария, последний не обязателен. 
**Просто жмём зеленую кнопку: создать


	Пункт 4:
$ git checkout master
**Будет написано, что ветка отстала. Ничего не делаем

$ edit "hello_world.cpp"
-----------------------------------
include <iostream>
include <string>

int main() 
{
    string str; // name :-(
    getline(std::cin, str); // read name (-_-)
    std::cout << "Hello World from " << str;
    return 0;
}
-----------------------------------
$ cat "hello_world.cpp" - проверка (выводит на консоль прогу)

$ git commit -am "Fixed coment"
$ git push -u origin patch2

Логин, пароль:
mkkazakova
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


	Пункт 5:
Необходимо проверить на GitHub в браузере наличие конфликта,
 кликнув на "lab-02" и выбрав вкладочку "Pull request". 
Там будет бело-голубая надпись о том, что есть конфликт
**Можно забить на этот пункт


	Пункт 6:
$ git pull origin master
$ git rebase master
$ edit "hello_world.cpp"

**Чуть-чуть меняем код
**Не допускается открывание кода вручную

$ git commit -am "Update code"


	Пункт 7:
$ git checkout patch2
$ git merge master
**Выводит конфликт
Auto-merging hello_world.cpp
CONFLICT (content): Merge conflict in hello_world.cpp
Automatic merge failed; fix conflicts and then commit the result.

$ git add "hello_world.cpp"
$ git commit -am "Last fix"
$ git push -f origin patch2

Логин, пароль:
mkkazakova
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

**Следует надпись о том, что всё обновлено


	Пункт 8:
Необходимо проверить на GitHub в браузере отсутствие конфликта,
 кликнув на "lab-02" и выбрав вкладочку "Pull request". 
Будет оранжевая надпись, которая станет зеленой
**Мой метод гарантированно лечит конфликт. Не забивать на этот пункт


	Пункт 9:
Нажимаем на зеленую надпись "Merge pull request" из предыдущего пункта 
и подтверждаем

