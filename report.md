## Отчет по лабораторной работе №5 по курсу «Информатика»
---
##### Ход работы

- Комадной  `git clone https://github.com/Seztor/Informatics-lab5.git`  клонируем себе репозиторий

- В директории `.git/hooks` создаем хук `pre-commit` который срабатывает перед коммитом

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
Он проверяет файлы формата .txt на то, что они не пустые, неподходящие файлы удаляются из "staging area"

