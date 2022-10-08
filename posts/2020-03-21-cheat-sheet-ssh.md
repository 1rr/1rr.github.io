---
layout: post
title: sheet
---

создание пользователя sudo

`sudo useradd -mUG sudo <name> sudo passwd <name>`

задать пароль для одноразового коннекта, чтоб пользователь мог загрузить свой ключ пользователь генерирует себе пару ключей: 

`ssh-keygen -t rsa -b 4096 -C "<name> @<name> " `

пользователь загружает свой ключ: 

`ssh-copy-id -i ~/.ssh/id_rsa.pub <name> @<host> `

Либо есть копирование с windows 

`mkdir ~/.ssh/ nano authorized_keys`

и вставить в него содержимое c локального компьютера 

`~/.ssh/id_rsa.pub`

Либо2 

`cat ~/.ssh/id_rsa.pub | ssh <name> @<host> -p 40120 "mkdir ~/.ssh; cat >> ~/.ssh/authorized_keys" `

любой sudoer выключает пароль для нового пользователя: s

`sudo passwd -d <name> `
