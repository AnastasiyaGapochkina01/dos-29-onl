> [!CAUTION]
> Это задание для самостоятельной работы — оно не будет отмечаться в lms и выходит за рамки курса
> 
> Сроки сдачи не ограничены, разбор решений/ответы на вопросы будут, но не в ущерб основной программе
> 
> В ТЗ и readme проекта _специально_ опущены некоторые подробности, чтобы вы поизучали то, что развернули

---

## Описание задачи
Команда anestesia.tech написала приложение на python, которое представляет собой трехкомпонентную систему для логирования, тестирования и анализа веб-приложений. Репозиторий проекта находится по ссылке -> [log-analize-python](https://github.com/AnastasiyaGapochkina01/log-analize-python).
В репозитории имеется описание проекта, в тч как каждый из компонентов запускается. Вам необходимо развернуть эту систему в соответствии с требованиями:
1) Операционная система - Ubuntu 20.04+ / Debian 11+
2) Python 3.11+
3) Присутствует виртуальное окружение (python virtualenv)
4) Установлены пакеты libpq-dev build-essential
5) Корневая директория проекта - /opt/web_monitoring
6) **API-сервер (log-server.py) и дашборд запущены с помощью systemd**
7) Для запуска скрипта генерации нагрузки можно использовать
- обычный ручной запуск
- bash-скрипт (в тч однострочник) как обертка
- cron для запуска по расписанию (ставьте небольшой промежуток, чтобы проверить и не забывайте убирать после успешной отработки)
- systemd сервис типа oneshot
8) Запуск от имени пользователя www-data
9) После запуска необходимо проверить работоспособность всех компонентов

## Шпаргалка

<details>
  <summary>Установка зависимостей</summary>
  
  ```bash
  sudo -u www-data python3 -m venv /opt/web_monitoring/.venv
  sudo -u www-data /opt/web_monitoring/.venv/bin/pip install -U -r requirements.txt
  ```
  
</details>

<details>
  <summary>Запуск из systemd</summary>
  
  ```bash
  ...
  WorkingDirectory=/opt/web_monitoring
  Environment="PATH=/opt/web_monitoring/.venv/bin/"
  ExecStart=/opt/web_monitoring/.venv/bin/python3 script.py
  ...
  ```
  
</details>
