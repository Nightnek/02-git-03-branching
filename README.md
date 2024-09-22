# Домашнее задание к занятию «Ветвления в Git»

## Задание «Ветвление, merge и rebase»

### Шаг 1.

Создайте в своём репозитории каталог branching и в нём два файла — merge.sh и rebase.sh — с содержимым
![image](https://github.com/user-attachments/assets/c659e938-b740-4c20-830f-438abc80849b)

### Шаг 2. 
Создадим коммит с описанием prepare for merge and rebase и отправим его в ветку main.
![image](https://github.com/user-attachments/assets/d69368b3-d560-4668-9f16-4a690e111772)


### Подготовка файла merge.sh

### Шаг 1. 
Создайте ветку git-merge.
![image](https://github.com/user-attachments/assets/11a81980-f4ca-4f71-84ff-4546e9d71639)


### Шаг 2. 
Замените в ней содержимое файла merge.sh на:
![image](https://github.com/user-attachments/assets/4a6cf9e3-79ca-42da-8ece-ce58c9f56bde)

### Шаг 3. 
Создайте коммит merge: @ instead *, отправьте изменения в репозиторий.
![image](https://github.com/user-attachments/assets/89b88ebb-c772-4b11-968d-462aff706016)

### Шаг 4. 
Разработчик подумал и решил внести ещё одно изменение в merge.sh
![image](https://github.com/user-attachments/assets/7674225c-4d01-4f36-8453-16be752fa3bd)

### Шаг 5.
Cоздайте коммит merge: use shift и отправьте изменения в репозиторий
![image](https://github.com/user-attachments/assets/05d4475c-29ae-4701-b1ac-323f5465d8dc)

### Изменим main

### Шаг 1. 
Вернитесь в ветку main. Шаг 2. Предположим, что пока мы работали над веткой git-merge, кто-то изменил main. Для этого изменим содержимое файла rebase.sh на:
![image](https://github.com/user-attachments/assets/87981110-0c56-4cac-855d-81a480551027)

В этом случае скрипт тоже будет отображать каждый параметр в новой строке.

### Шаг 3. 
Отправляем изменённую ветку main в репозиторий.
![image](https://github.com/user-attachments/assets/c31737f5-5624-4ed1-a9c9-d6e95a217a53)


### Подготовка файла rebase.sh
### Шаг 1. 
Предположим, что теперь другой участник нашей команды не сделал git pull либо просто хотел ответвиться не от последнего коммита в main, а от коммита, когда мы только создали два файла merge.sh и rebase.sh на первом шаге.
Для этого при помощи команды git log найдём хеш коммита prepare for merge and rebase и выполним git checkout на него так: git checkout 8baf217e80ef17ff577883fda90f6487f67bbcea (хеш будет другой). 
![image](https://github.com/user-attachments/assets/de9c4988-0bbc-4704-8299-e2436b886b5d)

### Шаг 2. 
Создадим ветку git-rebase, основываясь на текущем коммите. 
![image](https://github.com/user-attachments/assets/d5caffb9-d77e-488b-b832-e85a75625ebd)

### Шаг 3. 
И изменим содержимое файла rebase.sh на следующее, тоже починив скрипт, но немного в другом стиле:
![image](https://github.com/user-attachments/assets/1866bbcd-18e9-4f7c-92ed-a657aab6a844)

### Шаг 4. 
Отправим эти изменения в ветку git-rebase с комментарием git-rebase 1.
![image](https://github.com/user-attachments/assets/dd95f2b7-08a0-4cd4-8afa-10e87af2bd93)

### Шаг 5. 
И сделаем ещё один коммит git-rebase 2 с пушем, заменив echo "Parameter: $param" на echo "Next parameter: $param".
![image](https://github.com/user-attachments/assets/54245574-bff2-4d30-a318-15d8f1cbd438)
![image](https://github.com/user-attachments/assets/1c52ead6-3437-4e5d-9374-1b2e07d0446a)

Промежуточный итог
Мы сэмулировали типичную ситуации в разработке кода, когда команда разработчиков работала над одним и тем же участком кода, и кто-то из разработчиков предпочитает делать merge, а кто-то — rebase. Конфликты с merge обычно решаются просто, а с rebase бывают сложности, поэтому давайте смержим все наработки в main и разрешим конфликты.
![image](https://github.com/user-attachments/assets/985a2098-cc70-4d38-a166-399b3e5d4cfa)

Созданы обе ветки

### Merge
Сливаем ветку git-merge в main и отправляем изменения в репозиторий, должно получиться без конфликтов:
![image](https://github.com/user-attachments/assets/b31f0f4f-5ee0-4b36-b3e5-97e04694c642)

![image](https://github.com/user-attachments/assets/5aef4057-bb46-4418-8ac1-65be989532c5)


### Rebase
### Шаг 1. 
Перед мержем ветки git-rebase выполним её rebase на main. Да, мы специально создали ситуацию с конфликтами, чтобы потренироваться их решать. 
### Шаг 2. 
Переключаемся на ветку git-rebase и выполняем git rebase -i main. В открывшемся диалоге должно быть два выполненных коммита, давайте заодно объединим их в один, указав слева от нижнего fixup. В результате получаем:
![image](https://github.com/user-attachments/assets/286c4caa-f46f-4d51-be69-27d7437209fa)

### Шаг 3. 
Удалим метки, отдав предпочтение варианту:
![image](https://github.com/user-attachments/assets/cca5593e-00f8-400c-9309-b82068d480a3)


### Шаг 4. 
Сообщим Git, что конфликт решён git add rebase.sh и продолжим rebase git rebase --continue.
![image](https://github.com/user-attachments/assets/b9cd3f1f-ec11-4c49-a3d2-ea5748a5e1ed)

### Шаг 5. 
Опять получим конфликт в файле rebase.sh при попытке применения нашего второго коммита. Давайте разрешим конфликт, оставив строчку echo "Next parameter: $param".
![image](https://github.com/user-attachments/assets/203ca2dd-8158-4c7b-8fa0-776328a39627)

### Шаг 6. 
Далее опять сообщаем Git о том, что конфликт разрешён — git add rebase.sh — и продолжим rebase — git rebase --continue.
![image](https://github.com/user-attachments/assets/0bae5f7e-1246-48f1-ab3d-5e6dde8d92b0)


### Шаг 7.
И попробуем выполнить git push либо git push -u origin git-rebase, чтобы точно указать, что и куда мы хотим запушить.
Эта команда завершится с ошибкой:
![image](https://github.com/user-attachments/assets/83f1c61d-87f9-4fb8-b348-881ea2d97f1e)

Это произошло, потому что мы пытаемся перезаписать историю.

### Шаг 8. 
Чтобы Git позволил нам это сделать, добавим флаг force:
![image](https://github.com/user-attachments/assets/3c4b75a2-c56d-492a-8b31-d50708de89f5)


### Шаг 9. 
Теперь можно смержить ветку git-rebase в main без конфликтов и без дополнительного мерж-комита простой перемоткой:
![image](https://github.com/user-attachments/assets/f453f9bc-2305-4147-a0a8-d5863180262e)
![image](https://github.com/user-attachments/assets/62bb2a18-b41d-41fb-8e4e-288a430f9096)

