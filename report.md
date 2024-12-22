## Отчет по лабораторной работе №5 по курсу «Информатика»
---

### Задание 1

##### Ход работы

- Комадной  `git clone https://github.com/Seztor/Informatics-lab5.git`  клонируем себе репозиторий

- В директории `.git/hooks` создаем хук `pre-commit` который срабатывает перед коммитом

Он проверяет файлы формата .txt на то, что они не пустые, неподходящие файлы удаляются из "staging area"

Код:

```bash
#!/bin/bash
 
check_txt_file() {
    if [ ! -s "$1" ]; then
        echo "Ошибка: Файл $1 - пустой"
        git reset HEAD "$file"
    else
    	echo "Файл $1 успешно закоммичен"
    fi
 
}
 
files=$(git diff --cached --name-only --diff-filter=ACM | grep '\.txt$')
 
for file in $files; do
    if [ -f "$file" ]; then
        check_txt_file "$file"
    fi
done
 
exit 0
```
- Создаем для проверки два файла: пустой и не пустой                                                         
![image](https://github.com/user-attachments/assets/c66a413d-ffcf-4b58-88a3-dca77de0b368)

- Командой git add добавляем файлы в "staging area"                                                                      
![image](https://github.com/user-attachments/assets/e669fb89-687e-4d46-a10c-7096fa5f620a)

- Выполняем коммит                                                                                       
![image](https://github.com/user-attachments/assets/56307961-ed65-46e9-8cba-ff5ea42eb597)

- Результат: пустой файл вернулся в "changes", а непустой закомитился                                                    
![image](https://github.com/user-attachments/assets/19faaeed-dea6-446b-92e7-fd5938e6abd3)
![image](https://github.com/user-attachments/assets/34d5d765-44f2-43aa-b41d-55487bd71b47)

---

### Задание 2

- Инициализируем Git Flow
![image](https://github.com/user-attachments/assets/f504cbb0-bf6e-4df0-bd1f-00e8bce06ffe)

- Создаем новую ветку
![image](https://github.com/user-attachments/assets/8588b4bc-3b35-4c0e-b630-35cdb4d12265)

- Добавляем python file и коммитим его
![image](https://github.com/user-attachments/assets/a09a2039-e298-40dd-bdc4-920e8336888a)
![image](https://github.com/user-attachments/assets/b5c1fac0-ab4a-45ce-ab27-cc848604ffb9)

- Завершаем фичу и объединяем
![image](https://github.com/user-attachments/assets/c1b743b5-22e2-4879-b515-74984a508bef)

- Начинаем создание релиза
![image](https://github.com/user-attachments/assets/64e12fe0-d5e0-48fa-9032-a7f47dfdba30)

- Создаем hotfix и создаем файл python
![image](https://github.com/user-attachments/assets/cb9f4b49-992b-4a2a-918e-284c2545b432)
![image](https://github.com/user-attachments/assets/86fe1103-07b3-476a-88ee-d46827f53d46)

- Коммитим изменения и завершаем hotfix
![image](https://github.com/user-attachments/assets/cd99182c-80e1-4aac-a3ba-606d332e2863)

- Отправляем изменения на удаленный репозиторий
![Uploading image.png…]()
