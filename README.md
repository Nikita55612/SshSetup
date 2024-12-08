# sshSetup
Шпаргалка по настройке SSH: команды, конфигурации и настройка сервера.

## Сервер

Подключение  
ssh <имя_пользователя>@<IP-адрес>

Обновление системы
sudo apt update && sudo apt upgrade -y

Установите полезные пакеты
sudo apt install htop git curl wget -y

Создание пользователя
adduser <имя_пользователя>

Добавление пользователя в sudo группу
usermod -aG sudo <имя_пользователя>

Смена пользователя
su - <имя_пользователя>

Создание .ssh директории
sudo mkdir -p ~/.ssh

Устанавливаем права
sudo chmod 700 ~/.ssh
sudo chown <имя_пользователя>:<имя_пользователя> /home/<имя_пользователя>/.ssh

Создание файла authorized_keys
sudo touch ~/.ssh/authorized_keys

Устанавливаем права
sudo chmod 644 ~/.ssh/authorized_keys
