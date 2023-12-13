# Otus_6
Vagrant стенд для NFS

## Задача:
vagrant up должен поднимать 2 виртуалки: 

сервер и клиент;
на сервер должна быть расшарена директория;

на клиента она должна автоматически монтироваться при старте (fstab или autofs);

в шаре должна быть папка upload с правами на запись;

требования для NFS: NFSv3 по UDP, включенный firewall.

## Решение
Vagrant файл доступен по [ссылке](https://github.com/Sunabak/Otus_6/blob/main/Vagrantfile)

Скрипт для сервера nfss доступен по [ссылке](https://github.com/Sunabak/Otus_6/blob/main/nfss.sh)

Скрипт для сервера nfsс доступен по [ссылке](https://github.com/Sunabak/Otus_6/blob/main/nfsс.sh)

## Проверка после запуска стенда NFS
- заходим на сервер 

- заходим в каталог `/srv/share/upload` 

- создаём тестовый файл `touch check_file` 

```
maksimzv@maksimzvnb:~/Otus_6v1$ vagrant ssh nfss
[vagrant@nfss ~]$ cd /srv/share/upload
[vagrant@nfss upload]$ touch check_file
[vagrant@nfss upload]$ ls
check_file
````

- заходим на клиент 

- заходим в каталог `/mnt/upload` 

- проверяем наличие ранее созданного файла 

- создаём тестовый файл `touch client_file` 

- проверяем, что файл успешно создан 

```
[vagrant@nfsc ~]$ cd /mnt/upload
[vagrant@nfsc upload]$ ls
check_file
[vagrant@nfsc upload]$ touch client_file 
[vagrant@nfsc upload]$ ls
check_file  client_file
```
