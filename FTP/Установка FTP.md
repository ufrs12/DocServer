# Обновляем apt
 ```
 sudo apt update
 ```

# Устанавливаем vsftpd
 ```
 sudo apt install vsftpd
 ```

# Проверяем запустился ли
 ```
 sudo systemctl status vsftpd
 ```

# Если не запустилась, запускаем вручную
 ```
 sudo systemctl start vsftpd
 ```

# Устанавливаем запуск со стартом ОС
 ```
 sudo systemctl enable vsftpd
 ```

# Создаем пользователя ftpuser
 ```
 sudo adduser ftpuser
 ```

# Добавляем пользователя в разрешенные
 ```
 echo "ftpuser" | sudo tee -a /etc/vsftpd.userlist
 ```

# Создаем папку и настраиваем права на нее
 ```
 sudo mkdir -p /usr/share/soft/
 ```
 ```
 sudo chmod -R 750 /usr/share/soft/
 ```
 ```
 sudo chown -R ftpuser: /usr/share/soft/
 ```

# Настройка vsftpd
 ```
 sudo vim /etc/vsftpd.conf
 ```
 Доступ только для локальных пользователей:
    anonymous_enable=NO
    local_enable=YES

 Разрешения для локального пользователя:
    write_enable=YES
    chroot_local_user=YES
    allow_writeable_chroot=YES

# Перезагрузка
 ```
 sudo systemctl restart vsftpd
 ```

# Проверяем запустился ли
 ```
 sudo systemctl status vsftpd
 ```

# Доступ в файлзилле

Хост: sftp://сервер-IP
Имя пользователя: ftpuser
Пароль: Пароль пользователя ftpuser