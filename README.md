# SSH Setup  
Шпаргалка по настройке SSH: команды, конфигурации и настройка сервера.

---

## 📂 Содержание  
1. [Настройка сервера](#-настройка-сервера)  
2. [Настройка клиента](#-настройка-клиента)  
3. [Конфигурация SSHD](#-конфигурация-sshd)  
4. [Пример SSH Config](#-пример-ssh-config)  

---

## 🖥️ Настройка сервера  

### Подключение к серверу  
```bash
ssh <имя_пользователя>@<IP-адрес>
```

### Обновление системы  
```bash
sudo apt update && sudo apt upgrade -y
```

### Установка полезных пакетов  
```bash
sudo apt install htop git curl wget -y
```

### Создание пользователя  
```bash
adduser <имя_пользователя>
```

### Добавление пользователя в sudo группу  
```bash
usermod -aG sudo <имя_пользователя>
```

### Смена пользователя  
```bash
su - <имя_пользователя>
```

### Настройка SSH-директории  
```bash
sudo mkdir -p ~/.ssh
sudo chmod 700 ~/.ssh
sudo chown <имя_пользователя>:<имя_пользователя> /home/<имя_пользователя>/.ssh
```

### Создание и настройка файла `authorized_keys`  
```bash
sudo touch ~/.ssh/authorized_keys
sudo chmod 644 ~/.ssh/authorized_keys
```

---

## 💻 Настройка клиента  

### Создание SSH-ключа  
```bash
ssh-keygen -t ed25519
```

### Копирование публичного ключа  
Скопируйте ключ с помощью команды:  
```bash
cat ~/.ssh/id_ed25519.pub
```
Или используйте утилиту:  
```bash
ssh-copy-id <имя_пользователя>@<IP-адрес>
```

---

## 🔧 Конфигурация SSHD  

### Подключение к серверу  
```bash
ssh <имя_пользователя>@<IP-адрес>
```

### Вставка публичного ключа  
Откройте файл `authorized_keys`:  
```bash
sudo nano ~/.ssh/authorized_keys
```
Вставьте скопированный ключ.

### Редактирование конфигурации SSHD  
```bash
sudo -i
nano /etc/ssh/sshd_config
```

#### Измените и раскомментируйте следующие строки:  
```text
Port <Порт>
PermitRootLogin no
PasswordAuthentication no
AllowUsers <имя_пользователя>
```

### Перезагрузка SSHD  
```bash
sudo systemctl restart sshd
```

---

## 🛠️ Пример SSH Config  

Создайте файл `config` в директории `~/.ssh`:  
```bash
nano ~/.ssh/config
```

Пример содержимого:  
```text
Host server  
    HostName <IP-адрес>  
    Port <Порт>  
    User <имя_пользователя>  
    
Host *  
    IdentityFile ~/.ssh/key
```

---

🎉 Теперь ваш сервер готов к использованию через SSH!

