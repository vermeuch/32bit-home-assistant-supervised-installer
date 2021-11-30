[![hacs_badge](https://img.shields.io/badge/HAss-Default-blue.svg)](https://www.home-assistant.io/)
[![Donate](https://img.shields.io/badge/donate-Pizza-yellow.svg)](https://www.buymeacoffee.com/ntguest)
[![Donate](https://img.shields.io/badge/donate-Yandex-blueviolet.svg)](https://yoomoney.ru/to/410011383527168)

# 32bit-home-assistant-supervised-installer
Home Assistant supervised installer for 32bit systems

## Установка Home Assistant Supervised на Debian 11

Это руководство поможет вам установить Home Assistant Supervised практически на любой тип компьютера, включая нетбуки, неттопы и старые ПК с 32 битным процессором.

:warning: Используя Debian 11 и следуя строгому набору правил, доступных [ЗДЕСЬ](https://github.com/home-assistant/architecture/blob/master/adr/0014-home-assistant-supervised.md), вы получите поддерживаемую установку Home Assistant Supervised. Если вы в любой момент решите установить дополнительное программное обеспечение для операционной системы Debian, ваша установка станет официально не поддерживаемой. Однако поддержка доступна через форумы сообщества.

Несмотря на то, что были приложены все усилия, чтобы это руководство соответствовало [ADR-0014](https://github.com/home-assistant/architecture/blob/master/adr/0014-home-assistant-supervised.md), нет гарантии работоспособности в будущем.

В этом руководстве вы будете использовать Debian 11 в качестве операционной системы. Этот тип установки называется «безголовым», и после завершения установки вам не потребуется подключать клавиатуру, мышь или монитор, хотя вы можете это сделать, если хотите.

#### Что такое Home Assistant Supervised? ####

Home Assistant - это экосистема домашней автоматизации с полным пользовательским интерфейсом, в которой работают Home Assistant Core, Home Assistant Supervisor и надстройки. Он предустановлен в ОС Home Assistant, но может быть установлен в любой системе Linux. Он использует Docker, которым управляет Home Assistant Supervisor, плюс дополнительное преимущество десятков надстроек (например, магазин приложений), которые изначально работают в среде Home Assistant.

Если вы новичок в Home Assistant, теперь вы можете перейти к Разделу 1, если вам нужна помощь в установке Debian 11. Если у вас уже установлен Debian 11 и вы хотите перейти к установке Home Assistant, перейдите к Разделу 2.





## Раздел 1 - Установка Debian

<details>
  <summary> Если вам нужно пошаговое руководство по установке Debian 11 на ваш компьютер, щелкните здесь, чтобы просмотреть инструкции. </summary>


** 1.1) ** Начните с загрузки `debian-live-11.0.0-amd64-standard.iso` из [ЗДЕСЬ] (https://cdimage.debian.org/debian-cd/current-live/amd64/iso -гибридный/). Если вы предпочитаете полный образ Debain со всеми драйверами, загрузите `firmware-11.0.0-amd64-DVD-1.iso` [ЗДЕСЬ] (https://cdimage.debian.org/cdimage/unofficial/non-free/ cd-включая-firmware / 11.0.0 + nonfree / amd64 / iso-dvd / firmware-11.0.0-amd64-DVD-1.iso)

** 1.2) ** Пока Debian загружается, вам понадобятся другие программы, которые помогут с настройкой и установкой. Чтобы записать ISO-образ Debian на USB-накопитель, вы будете использовать программу под названием Rufus, которую можно загрузить с [ЗДЕСЬ] (https://rufus.ie/).

** 1.3) ** Теперь вы создадите загрузочный USB-накопитель, используя Rufus и образ Debian, который вы скачали. Вставьте в компьютер пустой USB-накопитель объемом не менее 8 ГБ, откройте Rufus и выберите USB-накопитель в раскрывающемся меню. Теперь выберите загруженный вами ISO-образ Debian и нажмите «Пуск». Если вы получите какие-либо запросы, выберите ОК или Да, чтобы продолжить. Когда это будет завершено, вы можете двигаться дальше.

** 1.4) ** Вставьте только что сделанный USB-накопитель в новую машину, подключите монитор, кабель Ethernet, клавиатуру и мышь и включите машину. Вам нужно будет выбрать USB-накопитель в качестве загрузочного устройства, для этого вам нужно будет нажать что-то вроде F12 или DEL на клавиатуре сразу после включения машины.

** 1.5) ** Первый экран, из которого вы можете выбрать, это ** Главное меню **, на этом экране выберите ** Графический установщик Debian **

** 1.6) ** Далее будет ** Язык **. Выберите свой язык и нажмите «Продолжить».

** 1.7) ** Далее будет ** Выберите ваше местоположение **. Выберите свою страну и нажмите «Продолжить».

** 1.8) ** Далее будет ** Настроить клавиатуру **. Выберите тип клавиатуры и нажмите «Продолжить». Теперь установщик выполнит некоторые автоматические задачи, которые займут 1-2 минуты.

** 1.9) ** Далее будет ** Настроить сеть **. Здесь вы можете назвать свою машину, имя по умолчанию будет `debian`. Выберите имя и нажмите «Продолжить». Вы можете пропустить следующую страницу, нажав «Продолжить», поскольку вам не нужно устанавливать доменное имя.

** 1.10) ** Далее будет ** Настройка пользователей и паролей **. Вам будет предложено создать пароль для пользователя root. Запишите пароль, который вы здесь выбрали, и нажмите «Продолжить».

** 1.11) ** Далее будет ** Настроить пользователей и пароли ** снова. Введите имя пользователя, нажмите «Продолжить» и на следующем экране введите пароль для этой учетной записи. Обратите внимание на оба этих параметра, они понадобятся вам позже.

** 1.12) ** Далее будет ** Настроить часы **. Выберите правильный часовой пояс и нажмите «Продолжить».

** 1.13) ** Далее будет ** Разделить диски **. Выберите ** Управляемый - использовать весь диск **, а затем нажмите «Продолжить». На следующем экране убедитесь, что выбран правильный диск, и нажмите «Продолжить». На следующем экране выберите ** Все файлы в одном разделе ** и нажмите «Продолжить». На следующем экране убедитесь, что ** Завершить часть
</details>

## Раздел 2 - Установка Home Assistant Supervised

Шаг 1: Установите следующие зависимости с помощью этих команд:

```bash
su -
apt update && apt upgrade -y && apt autoremove -y
apt-get install software-properties-common apparmor-utils apt-transport-https ca-certificates curl dbus jq network-manager wget udisks2 libglib2.0-bin unzip -y
```

Шаг 2: Остановите и отключите Modem Manager:

```bash
systemctl disable ModemManager
systemctl stop ModemManager
```

Шаг 3: Установите Docker-IO:

```bash
apt install -y docker.io
```

Step 4: Установите OS-Agent:

```bash
wget https://github.com/home-assistant/os-agent/releases/download/1.2.2/os-agent_1.2.2_linux_i386.deb
dpkg -i os-agent_1.2.2_linux_i386.deb
```

Актуальные инструкции по установке OS-Agent заходятся [ЗДЕСЬ](https://github.com/home-assistant/os-agent/tree/main#using-home-assistant-supervised-on-debian)

Step 5: Запустите скрипт установки Home Assisistant Supervised Debian:

```bash
curl -sL "https://raw.githubusercontent.com/ntguest/32bit-home-assistant-supervised-installer/master/files/installer-ru.sh" | bash -s -- -m qemux86
```

Также этот скрипт можно использовать и для других типы машин
```
- generic-x86-64
- odroid-c2
- odroid-n2
- odroid-xu
- qemuarm
- qemuarm-64
- qemux86
- qemux86-64
- raspberrypi
- raspberrypi2
- raspberrypi3
- raspberrypi4
- raspberrypi3-64
- raspberrypi4-64
- tinker
- khadas-vim3
```  
Следуйте инструкциям на экране

## Раздел 3 - Установка ESPHome

<details>
  <summary> К превеликой скорби 32-битный аддон ESPHome не существует в природе, но если вам нужен, его можно установить в виртуальное окружение. Инструкция под катом.</summary>


  Шаг 1: Установите следующие зависимости с помощью этих команд:

  ```bash  
export PATH=$PATH:/usr/sbin
apt-get sudo install python3-dev python3-venv python3-pip libffi-dev libssl-dev -y
  ```
  Шаг 2: Добавьте пользователя, папки и права:
  ```bash  
useradd -rm esp -G dialout
cd /srv
mkdir esp
chown esp:esp esp
  ```

  ```bash 
sudo -u esp -H -s
cd /srv/esp
python3 -m venv .
source bin/activate
python3 -m pip install wheel
export CRYPTOGRAPHY_DONT_BUILD_RUST=1
pip install cryptography==3.1.1
pip3 install esphome
  ```

  ```bash 
exit
cd /usr/share/hassio/homeassistant
mkdir esphome
chown esp:esp esphome
  ```
  
  ```bash
nano /etc/systemd/system/esphome.service
  ```
  
  ```
[Unit]
Description=Esphome
After=network.target
[Service]
Environment=PATH=/srv/esp/bin:/usr/sbin:/usr/bin:/sbin:/bin
Type=simple
User=root
WorkingDirectory=/usr/share/hassio/homeassistant/esphome
ExecStart=/srv/esp/bin/esphome config/ dashboard
Restart=always
[Install]
WantedBy=multi-user.target
  ```
  
  ```
  CTRL+O и CTRL+X
  ```
  
  ```bash
systemctl --system daemon-reload
systemctl enable esphome.service
systemctl start esphome.service
  ```
  
  ```bash
su -
sudo -u esp -H -s
cd /srv/esp
source bin/activate
pip3 install -U esphome
exit
systemctl restart esphome.service
  ```
</details>

## Раздел 4 - Установка HACS

```bash
curl -sfSL https://hacs.xyz/install | bash -
```
