1) Установить Jenkins на ВМ
2) Ознакомиться с дополнительным материалом ([ссылка]())
3) Написать простой пайплайн `todoapp-php ci/cd`, состоящий из этапов:
- initialize - этап выводит приветственное сообщение "Start testing ToDo app; Build ${BUILD_NUMBER}"
- checkout - этап клонирует репозиторий https://github.com/AnastasiyaGapochkina01/simplest-todo
- test - этап проводит тестирование кода; команда `phpunit --log-junit test-results.xml` (**!! ВАЖНО: тесты могут падать**)
- finish - этап выводит завершающее сообщение "Tests finished"

4) Добавить к пайплайну `todoapp-php ci/cd` этап build image; этап должен запускаться _только если при запуске был отмечен checkbox 'Build image'_; 
image tag должен передаваться в виде строки при запуске билда, значение по умолчанию - latest
5) Добавить к пайплайну `todoapp-php ci/cd` checkbox 'push image to docker hub' и этап, который будет пушить собранный docker image в ваш репозиторий на dockerhub, если checkbox отмечен
6) Добавить к пайплайну `todoapp-php ci/cd` этап 'Clean', который будет 
- удалять папку с проектом
- удалять все неиспользуемые docker images
7) Добавить к пайплайну `todoapp-php ci/cd` этап 'deploy', который будет деплоить собранный image на удаленный хост
