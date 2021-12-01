[![hacs_badge](https://img.shields.io/badge/HAss-Installer-blue.svg)](https://www.home-assistant.io/)
[![Donate](https://img.shields.io/badge/donate-Pizza-yellow.svg)](https://www.buymeacoffee.com/ntguest)
[![Donate](https://img.shields.io/badge/donate-Yandex-blueviolet.svg)](https://yoomoney.ru/to/410011383527168)

# 32bit-home-assistant-supervised-installer
Home Assistant supervised installer for 32bit systems
Описание на русском языке доступно [ЗДЕСЬ](https://github.com/ntguest/32bit-home-assistant-supervised-installer/blob/main/README-RUSSIAN.md)

## Installing Home Assistant Supervised on Debian 11

This guide will help you to install Home Assistant Supervised, on almost any machine type you choose, even netbooks, nettops and old PCs with 32bit CPU. 

:warning: Using Debian 11 and following a strict set of guidelines available [HERE](https://github.com/home-assistant/architecture/blob/master/adr/0014-home-assistant-supervised.md) will give you a supported installation of Home Assistant Supervised. If you choose at anytime to install additional software to the Debian operating system, your installation will become officially unsupported. Community support via the forums is always available however.

While every effort has been made to ensure this guide complies with [ADR-0014](https://github.com/home-assistant/architecture/blob/master/adr/0014-home-assistant-supervised.md), no guarantee can be made it does now, or in the future.

In this guide, you will be using Debian 11 as the operating system. This type of installation is what is called “headless” and after the installation is complete, you will not need to have a keyboard, mouse or monitor attached, although you can if you prefer.

#### What is Home Assistant Supervised? ####

Home Assistant is a full UI managed home automation ecosystem that runs Home Assistant Core, the Home Assistant Supervisor and add-ons. It comes pre-installed on Home Assistant OS, but can be installed on any Linux system. It leverages Docker, which is managed by the Home Assistant Supervisor plus the added benefit of dozens of add-ons (think app store) that work natively inside the Home Assistant environment.

If you are new to Home Assistant, you can now proceed to Section 1 if you need assistance with installing Debian 11. If you already have Debian 11 installed and wish to move on to installing Home Assistant, move on to Section 2.





## Раздел 1 - Установка Debian

Для Debian существует [крошечный образ](https://deb.debian.org/debian/dists/Debian11.1/main/installer-i386/current/images/netboot/mini.iso), который имеет размер всего 41 мб. Там находятся самый минимум, который позволяет запустить процесс установки и скачать все необходимое из сети в процессе. Записываем его любой программой для записи образов на флешку, вставляем ее в свой ПК и устанавливаем в BIOS загрузку с USB.

<details>
  <summary> If you would like a step by step guide on how to install Debian 11 to your machine, click here to expand for instructions. </summary>


Простота процесса установки Debian позволяет в нескольких картинках показать практически все. Пробежимся бегло.
  
  
![VirtualBox_test_17_03_2021_23_31_42](https://user-images.githubusercontent.com/69485846/144154022-35236a2e-6a84-4e5e-85e7-2370dfdd71ee.png)
  
  Нажимаем Enter
  
![VirtualBox_test_17_03_2021_23_32_48](https://user-images.githubusercontent.com/69485846/144154024-7329dfda-fdd1-455b-968e-ee7dd0e3b035.png)
  
  Выбираем язык
  
![VirtualBox_test_17_03_2021_23_33_09](https://user-images.githubusercontent.com/69485846/144154025-d9ea0814-01bd-40de-b59e-08d8f25298c0.png)
  
  Страну
  
![VirtualBox_test_17_03_2021_23_33_30](https://user-images.githubusercontent.com/69485846/144154027-c37b3cf9-81c7-4f69-b3ab-e319744a940c.png)
  
  Раскладку клавиатуры
  
![VirtualBox_test_17_03_2021_23_33_44](https://user-images.githubusercontent.com/69485846/144154028-51a31699-748d-4dce-8f1a-288a03bf9055.png)
  
  Комбинацию клавиш, для переключения раскладки
  
![VirtualBox_test_17_03_2021_23_34_37](https://user-images.githubusercontent.com/69485846/144154029-db5ee106-d8c7-466f-8af0-e993d351338a.png)
  
  Придумываем прикольное имя компьютера
  
![VirtualBox_test_17_03_2021_23_35_07](https://user-images.githubusercontent.com/69485846/144154030-d293820e-fa62-4a32-a3d9-1f2d68fb4cb5.png)
  
  Жмем Enter
  
![VirtualBox_test_17_03_2021_23_35_20](https://user-images.githubusercontent.com/69485846/144154031-2e0d4668-fe6f-4629-bd05-5b3b674842fb.png)
  
  Еще раз
  
![VirtualBox_test_17_03_2021_23_42_39](https://user-images.githubusercontent.com/69485846/144154033-713cf51b-7b64-40aa-8626-187a8c4adbfd.png)
  
  Используем весь диск
  
![VirtualBox_test_17_03_2021_23_43_06](https://user-images.githubusercontent.com/69485846/144154035-707e42a5-8e14-4647-9eaa-28da3bc2dadc.png)
  
  И один раздел
  
![VirtualBox_test_17_03_2021_23_43_27](https://user-images.githubusercontent.com/69485846/144154037-19e52d60-7362-41c9-9f57-1f00109960c7.png)
  
  Записываем изменения на диск
  
![VirtualBox_test_17_03_2021_23_50_33](https://user-images.githubusercontent.com/69485846/144154040-58ea82d4-1490-40e6-8afd-14bbcec39c19.png)
  
  Я ставлю только SSH. Остальное по желанию.
  
![VirtualBox_test_17_03_2021_23_52_06](https://user-images.githubusercontent.com/69485846/144154041-7a2634c9-177b-4d19-aae0-c5eb6bc0e32b.png)
  
  И последний раз Enter
  
  
  С установкой закончили. Если я что-то и попустил, то все достаточно понятно и задокументировано в сети.
  
</details>

## Section 2 – Install Home Assistant Supervised

With Debian installed, you can move on to installing Home Assistant Supervised.

Step 1: First you will start by updating the Debian OS to make sure all the latest updates, security patches and nessesary dependacy's are installed. To do this, log into the terminal of your machine, enter the following command and press enter.
```bash
su -
```
```bash
apt update && apt upgrade -y && apt autoremove -y
apt-get install software-properties-common apparmor-utils apt-transport-https ca-certificates curl dbus jq network-manager wget udisks2 libglib2.0-bin unzip -y
```

Step 2: Stop and disable Modem Manager:

```bash
systemctl disable ModemManager
systemctl stop ModemManager
```

Step 3: Install Docker-IO:

```bash
apt install -y docker.io
```

Step 4: Install OS-Agent:

```bash
wget https://github.com/home-assistant/os-agent/releases/download/1.2.2/os-agent_1.2.2_linux_i386.deb
dpkg -i os-agent_1.2.2_linux_i386.deb
```

Instructions for installing the OS-Agent can be found [here](https://github.com/home-assistant/os-agent/tree/main#using-home-assistant-supervised-on-debian)


Step 5: Start script to install Home Assisistant Supervised:

```bash
curl -sL "https://raw.githubusercontent.com/ntguest/32bit-home-assistant-supervised-installer/master/files/installer.sh" | bash -s -- -m qemux86
```

Also supported next Machine types:
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
Follow instructions

## Section 3 - Install ESPHome

<details>
  <summary> Owners of 64bit machines can pass this section. Addon on Home Assistant Supervised require only 64bit but we can install esphome into virtual enviroment.</summary>


  Step 1: Install the following dependacy's with this command:

  ```bash  
export PATH=$PATH:/usr/sbin
apt-get install sudo python3-dev python3-venv python3-pip libffi-dev libssl-dev -y
  ```

  Step 2: Add user, folders and rights:
  
  ```bash  
useradd -rm esp -G dialout
cd /srv
mkdir esp
chown esp:esp esp
  ```

  Step 3: Install ESPHome 
  ```bash 
sudo -u esp -H -s
cd /srv/esp
python3 -m venv .
source bin/activate
  ```
  ```bash
python3 -m pip install wheel
export CRYPTOGRAPHY_DONT_BUILD_RUST=1
pip install cryptography==3.1.1
pip3 install esphome
exit
  ```

  Step 4: Add working folder and rights

  ```bash 
cd /usr/share/hassio/homeassistant
mkdir esphome
chown esp:esp esphome
  ```
  
  Step 5: Install service
  
  Start nano editor
  
  ```bash
nano /etc/systemd/system/esphome.service
  ```
  
  Next block copy and paste into editor
  
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
  
  To finish press
  
  ```
  CTRL+O, Enter and CTRL+X
  ```
  
  Enable service
  ```bash
systemctl --system daemon-reload
systemctl enable esphome.service
  ```
  ESPHome panel you can add as Lovelace iframe panel with servers IP and port 6052
  
## Later you can update esphome with this commands:

  ```bash
su -
  ```
  ```bash
sudo -u esp -H -s
cd /srv/esp
source bin/activate
pip3 install -U esphome
exit
systemctl restart esphome.service
  ```
</details>

## Section 4 - Install HACS

It's really simle. Дождитесь появления окна установки пароля Ноme Assistant. Можно ничего не вводить, переключиться обратно в терминал и:

```bash
curl -sfSL https://hacs.xyz/install | bash -
reboot
```

System will reboot and you can find HACS in integrations. 


## Теперь можно вводить пользователя и пользоваться

<details>
<summary> What you will get  </summary> 

  ![image](https://user-images.githubusercontent.com/69485846/144156382-cf0f055c-edfe-4bc2-aa84-bef95268eb70.png)
  ![image](https://user-images.githubusercontent.com/69485846/144156782-8f31cd4b-b046-4622-a6ef-6a286027bc26.png)

  </details>
  
  
And of course [<img src="https://www.buymeacoffee.com/assets/img/guidelines/download-assets-2.svg" alt="BuyMeACoffee" width="100">](https://www.buymeacoffee.com/ntguest)    or    [<img src="https://hsto.org/getpro/geektimes/post_images/7a9/b88/258/7a9b882584c6ea6ed1f48e96be00a187.png" width="100">](https://yoomoney.ru/to/410011383527168)
