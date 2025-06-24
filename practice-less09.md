### Задача
Развернуть Python-веб-сервер, настроить управление через systemd, организовать логирование; проверка `curl http://localhost:8000`

Код сервера
```python
from http.server import SimpleHTTPRequestHandler, HTTPServer
import os

os.chdir("/srv/webapp/content")
server = HTTPServer(('0.0.0.0', 8000), SimpleHTTPRequestHandler)
server.serve_forever()
```

#### Требования
1) Сервер запущен как systemd демон с правами пользователя `webadmin`
2) Пользователь `webadmin` не имеет shell-доступпа и является членом группы `webgroup`
3) Код сервера расположен в директории `/opt/srv/webapp`; в той же диреткории лежит `content/index.html` с содержимым
```html
<!DOCTYPE html>
<html>
<head>
    <title>Приветствие</title>
    <style>
        .greeting {
            border: 5px solid orange; 
            padding: 20px; 
            font-size: 48px;
            text-align: center; 
            margin: 50px auto; 
            width: fit-content;
            border-radius: 15px;
            background-color: #fff8f0; 
            font-family: Arial, sans-serif;
            box-shadow: 0 0 15px rgba(255, 165, 0, 0.3); 
        }
    </style>
</head>
<body>
    <div class="greeting">Привет, мир!</div>
</body>
</html>
```
4) Настроено логрование в syslog/rsyslog
