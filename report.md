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

---

### Задание 2
