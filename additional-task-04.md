# Занятия №11 и №12: Bash/Shell
Скрипт по проверке сертификатов: https://gist.github.com/AnastasiyaGapochkina01/7e2769368c234811707a8a847f672e20

Скрипт по проверке и рестарту сервисов: https://gist.github.com/AnastasiyaGapochkina01/6bcd2230894f2ebb15e7c21087e0c4ec

## Регулярные выражения
1) Написать регулярное выражение, с помощью которого из файла `apache2-error.log` можно получить
- ip-адрес клиента
- сервис, от которого был ответ
- loglevel

Пример файла `apache2-error.log`
```log
[Sun Jan 19 10:00:01.123456 2025] [core:error] [pid 1234:tid 140123456789824] [client 192.168.1.1:12345] Directory index forbidden by Options directive: /var/www/html/
[Sun Jan 19 10:00:02.123456 2025] [php:error] [pid 1234:tid 140123456789824] [client 192.168.1.1:12345] PHP Warning:  include(nonexistent.php): failed to open stream: No such file or directory in /var/www/html/index.php on line 10
[Sun Jan 19 10:00:03.123456 2025] [core:error] [pid 1234:tid 140123456789824] [client 192.168.1.2:54321] File does not exist: /var/www/html/favicon.ico
[Sun Jan 19 10:00:04.123456 2025] [authz_core:error] [pid 1234:tid 140123456789824] [client 192.168.1.3:67890] AH01630: client denied by server configuration: /var/www/html/private/
[Sun Jan 19 10:00:05.123456 2025] [core:error] [pid 1234:tid 140123456789824] [client 192.168.1.4:13579] Premature end of script headers: cgi-bin/script.cgi
```
2) Написать регулярное выражение, с помощью которого из файла `colors.conf` можно получить только коды цветов в шестнадцатеричном формате. Пример файла `colors.conf` 
```conf
White	#FFFFFF	255,255,255
Black	0,0,0 #000000
Red	#FF0000	255,0,0
Green	#00FF00	0,255,0
Blue	#0000FF	0,0,255
```
3) Написать пайплайн, с помощью которого из файла `auditd.log` можно получить количество сообщений от каждого типа сервиса
Пример файла `auditd.log`
```log
type=CRED_DISP msg=audit(1737696084.384:13): pid=2250 uid=1000 auid=1000 ses=1 subj=unconfined msg='op=PAM:setcred grantors=pam_permit acct="root" exe="/usr/bin/sudo" hostname=? addr=? terminal=/dev/pts/0 res=success'^]UID="anestesia" AUID="anestesia"
type=USER_ACCT msg=audit(1737696093.513:14): pid=2485 uid=1000 auid=1000 ses=1 subj=unconfined msg='op=PAM:accounting grantors=pam_permit acct="anestesia" exe="/usr/bin/sudo" hostname=? addr=? terminal=/dev/pts/0 res=success'^]UID="anestesia" AUID="anestesia"
type=USER_CMD msg=audit(1737696093.513:15): pid=2485 uid=1000 auid=1000 ses=1 subj=unconfined msg='cwd="/etc/promtail" cmd=6C73202F7661722F6C6F672F61756469742F exe="/usr/bin/sudo" terminal=pts/0 res=success'^]UID="anestesia" AUID="anestesia"
type=CRED_REFR msg=audit(1737696093.513:16): pid=2485 uid=1000 auid=1000 ses=1 subj=unconfined msg='op=PAM:setcred grantors=pam_permit acct="root" exe="/usr/bin/sudo" hostname=? addr=? terminal=/dev/pts/0 res=success'^]UID="anestesia" AUID="anestesia"
type=USER_START msg=audit(1737696093.513:17): pid=2485 uid=1000 auid=1000 ses=1 subj=unconfined msg='op=PAM:session_open grantors=pam_permit,pam_unix acct="root" exe="/usr/bin/sudo" hostname=? addr=? terminal=/dev/pts/0 res=success'^]UID="anestesia" AUID="anestesia"
type=USER_END msg=audit(1737696093.517:18): pid=2485 uid=1000 auid=1000 ses=1 subj=unconfined msg='op=PAM:session_close grantors=pam_permit,pam_unix acct="root" exe="/usr/bin/sudo" hostname=? addr=? terminal=/dev/pts/0 res=success'^]UID="anestesia" AUID="anestesia"
type=CRED_DISP msg=audit(1737696093.517:19): pid=2485 uid=1000 auid=1000 ses=1 subj=unconfined msg='op=PAM:setcred grantors=pam_permit acct="root" exe="/usr/bin/sudo" hostname=? addr=? terminal=/dev/pts/0 res=success'^]UID="anestesia" AUID="anestesia"
type=USER_ACCT msg=audit(1737696109.427:20): pid=2496 uid=1000 auid=1000 ses=1 subj=unconfined msg='op=PAM:accounting grantors=pam_permit acct="anestesia" exe="/usr/bin/sudo" hostname=? addr=? terminal=/dev/pts/0 res=success'^]UID="anestesia" AUID="anestesia"
type=SYSCALL msg=audit(1737696144.264:35): arch=c000003e syscall=257 success=yes exit=3 a0=ffffff9c a1=7f17b5c4715e a2=80000 a3=0 items=1 ppid=619 pid=2511 auid=1000 uid=1000 g
id=1000 euid=0 suid=0 fsuid=0 egid=1000 sgid=1000 fsgid=1000 tty=pts0 ses=1 comm="sudo" exe="/usr/bin/sudo" subj=unconfined key="passwd"^]ARCH=x86_64 SYSCALL=openat AUID="anestesia" UID="anestesia" GID="anestesia" EUID="root" SUID="root" FSUID="root" EGID="anestesia" SGID="anestesia" FSGID="anestesia"
type=CWD msg=audit(1737696144.264:35): cwd="/etc/promtail"
type=PATH msg=audit(1737696144.264:35): item=0 name="/etc/passwd" inode=29389 dev=fe:02 mode=0100644 ouid=0 ogid=0 rdev=00:00 nametype=NORMAL cap_fp=0 cap_fi=0 cap_fe=0 cap_fver=0 cap_frootid=0^]OUID="root" OGID="root"
type=PROCTITLE msg=audit(1737696144.264:35): proctitle=7375646F00617564697463746C002D6C
type=SYSCALL msg=audit(1737696144.264:36): arch=c000003e syscall=257 success=yes exit=5 a0=ffffff9c a1=7f17b5c4715e a2=80000 a3=0 items=1 ppid=619 pid=2511 auid=1000 uid=1000 gid=1000 euid=0 suid=0 fsuid=0 egid=1000 sgid=1000 fsgid=1000 tty=pts0 ses=1 comm="sudo" exe="/usr/bin/sudo" subj=unconfined key="passwd"^]ARCH=x86_64 SYSCALL=openat AUID="anestesia" UID="anestesia" GID="anestesia" EUID="root" SUID="root" FSUID="root" EGID="anestesia" SGID="anestesia" FSGID="anestesia"
type=CWD msg=audit(1737696144.264:36): cwd="/etc/promtail"
type=PATH msg=audit(1737696144.264:36): item=0 name="/etc/passwd" inode=29389 dev=fe:02 mode=0100644 ouid=0 ogid=0 rdev=00:00 nametype=NORMAL cap_fp=0 cap_fi=0 cap_fe=0 cap_fver=0 cap_frootid=0^]OUID="root" OGID="root"
```
4) Написать пайплайн с помощью которого из файла `app.log` можно получить записи о подключении к БД и из них ip адрес, по которому идет подключение. Пример файла `app.log`
```log
2025-02-01 10:00:00 - INFO - Application started successfully.
2025-02-01 10:05:23 - WARNING - Low disk space on drive C:.
2025-02-01 10:15:45 - ERROR - Failed to connect to the database 10.3.1.5:3306. Retrying...
2025-02-01 10:20:10 - INFO - Successfully connected to the database 10.3.1.5:3306.
2025-02-01 11:00:00 - INFO - User logged in: user@example.com.
2025-02-01 11:05:30 - INFO - Data export completed successfully.
2025-02-01 11:30:15 - WARNING - High memory usage detected.
2025-02-01 12:00:00 - INFO - Application stopped.
```

## Скрипты
1) Написать bash скрипт, проверяющий работоспособность любого сайта (или сайтов). Домен (домены) передаются как аргументы. А за работоспособность сайта примем коды ответа 2xx и 3xx
2) Написать скрипт для поиска свободного порта из диапазона M-N, где M и N - передаются скрипту как аргументы
3) Написать скрипт для проверки соответствия пароля политикам безопасности:
- количество символов от 12 до 24
- обязательно содержит буквы верхнего и нижнего регистра
- минимум одна цифра
- минимум один спец. символ
## 
