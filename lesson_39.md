# I
1) Создать облачную сеть `dos-29-network`.
2) Добавить в `dos-29-network` подсеть `diplom-dev-subnet` с CIDR 192.168.1.0/24
3) Создать ВМ `dimplom-dev-vm-1`:
- ресурсы: 2 vCPU, 2 ГБ RAM
- образ ubuntu 24.04
- приватный IP из подсети `diplom-dev-subnet`; публичный IP включён
- добавлены два пользователя:
    - ваш пользователь
    - пользователь `deployer` (для дальнейших задач автоматизации)
- добавлен вывод публичного IP-адреса ВМ после создания (изучить `outputs`)
# II
1) Создать бакет `tf-state-dev`.
2) Настроить backend terraform для хранения tfstate в Object Storage.
# III
1) В облачную сеть `dos-29-network` добавить подсеть `diplom-prod-subnet` CIDR 10.20.0.0/24
2) Создать две ВМ (ресурсы одинаковые, на свой выбор)
- `dimplom-prod-balancer-1`:
    - добавить к ВМ provisioner для установки nginx (inline)
    - сделать конфиг nginx для проксирования на бэкенд и тоже через provisioner подсунуть его nginx
- `dimplom-prod-backend-1`
    - добавить к ВМ provisioner для копирования скрипта по разворачиванию бэкенда (скрипт можно взять тут https://gist.github.com/AnastasiyaGapochkina01/271e526495c94a74efd85b7154b2d3db)
