1) Создать скрипт для мониторинга активных SSH-сессий с оповещением о подозрительной активности. Требования: Выводит список пользователей с >2 активными сессиями Проверяет подключения с недоверенных IP (из файла `blocklist.txt`) Логирует подозрительные события в `/var/log/auth_audit.log` Формат лога: 
```
[Дата] [Пользователь] [IP] [Кол-во сессий]
```
2) Создать скрипт для резервного копирования PostgreSQL
3) Написать скрипт, для деплоя лендинга https://gitlab.com/dos-26/cmdb/frontend и скрипт для его проверки
4) Написать скрипт для мониторинга даты продления доменного имени
