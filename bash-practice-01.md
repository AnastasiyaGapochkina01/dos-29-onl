1) Напишите скрипт, который запрашивает имя пользователя и выводит персонализированное приветствие.
<details>
  <summary>Вариант реализации</summary>
  
  ```bash
  #!/bin/bash
  echo "Как вас зовут?"
  read name
  echo "Привет, $name! Добро пожаловать в мир Bash!"
  ```
  
</details>

2) Попросите пользователя ввести число и определите, чётное оно или нечётное.
<details>
  <summary>Вариант реализации</summary>
  
  ```bash
  #!/bin/bash
  echo "Введите число:"
  read number
  if (( number % 2 == 0 )); then
    echo "$number — чётное число"
  else
    echo "$number — нечётное число"
  fi
  ```
  
</details>

3) Запросите у пользователя число N и выведите все числа от 1 до N включительно.
<details>
  <summary>Вариант реализации</summary>
  
  ```bash
  #!/bin/bash
  echo "Введите число N:"
  read n
  for (( i=1; i<=n; i++ )); do
    echo $i
  done
  ```
  
</details>

4) Напишите скрипт, который принимает расширение файла (например, txt) в качестве аргумента, ищет все файлы с этим расширением в текущей директории
<details>
  <summary>Вариант реализации</summary>
  
  ```bash
  #!/bin/bash

  if [ $# -eq 0 ]; then
    echo "Ошибка: Укажите расширение файла (например: ./script.sh txt)"
    exit 1
  fi

  ext="$1"
  files=( *."$ext" )

  if [ ${#files[@]} -eq 0 ]; then
    echo "Файлы с расширением .$ext не найдены"
    exit 0
  fi

  # Статистика
  echo "Найдено файлов: ${#files[@]}"
  ```
  
</details>

5) Написать скрипт, который проверяет использование диска для корневой директории (/) и выводит предупреждение, если свободного места меньше указанного порога (в %). Порог задается как аргумент.
<details>
  <summary>Вариант реализации</summary>
  
  ```bash
  #!/bin/bash

  if [ $# -eq 0 ]; then
    echo "Укажите порог в % (например: ./disk_check.sh 10)"
    exit 1
  fi

  threshold="$1"
  usage=$(df -h / | tail -1 | awk '{print $5}' | tr -d '%')

  if [ "$usage" -ge "$threshold" ]; then
    echo "ВНИМАНИЕ! Свободного места осталось: $((100 - usage))%"
    echo "Текущее использование: $usage% (порог: $threshold%)"
  else
    echo "Статус в норме. Использование: $usage% (порог: $threshold%)"
  fi
  ```
  
</details>
