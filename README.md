# 4IZ562 Řízení kvality dat

## Zadání úlohy

### Audit kvality dat
* Technický profiling: s pomocí vybraného nástroje vytvořte profilaci dat (základní popisné statistiky, četnosti syntaktických vzorů, ...)
* Validace vybraných atributů pomocí regulárních výrazů, kontrolních součtů, lookup a business pravidel
* Spočtěte úroveň kvantitativních vlastností dat (správnost, úplnost, konzistentnost, ...)
* Root-cause analýza zjištěných defektů
* Na příkladu modelové firmy odhadněte roční výši nákladů na nekvalitní data
* Porovnejte možné přínosy nápravných opatření se souvisejícími náklady
* Proveďte prioritizaci nápravných opatření
* Navrhněte externí datové zroje pro obohacení dat
* Navrhněte strategii pro doplnění chybějících hodnot
* Odevzdání vypracované zprávy auditora + naměřené charakteristiky / náklady

### Implementace doporučených opatření
* Optimalizace datového modelu
* Parsing adresy, standardizace, vytvoření porovnávacích kódů a zřetězení na adresní registr
* Nastavení příznaku doručitelnosti na adresu na základě pravidel
* Doplnění chybějících pozorování
* Unifikace dat klientů, adres, kontaktů
* Deduplikace klientů
* Návhr kontrol bránících dalšímu vzniku chyb v datech
* Odevzdání CSV souborů s vyčištěnými daty

## Lab

Pro vypracování semestrální práce potřebujete data modelové firmy dostupné jako SQL dump z MySQL / MariaDB databáze. SQL soubor chráněný heslem je dostupný z adresáře [data](data/4iz562.zip).

Doporučené nástroje pro vypracování semestrální práce: MySQL Server, Python + Jupyter Lab, Talend Open Studio for Data Quality [https://sourceforge.net/projects/talendprofiler/](https://sourceforge.net/projects/talendprofiler/)

Alternativní postupy pro vytvoření experimentálního prostředí jsou shrnuty v následujících odstavcích: 

### VirtualBox VM

* Nainstalujte VirtualBox z [https://www.virtualbox.org/](https://www.virtualbox.org/)
* Stáhněte si iso Ubuntu Focal Fossa Desktop z [https://www.releases.ubuntu.com/20.04/](https://www.releases.ubuntu.com/20.04/)
* Vytvořte nove VM s alespoň 2 CPU, 8GB RAM a 20-30 GB VDI
* Nainstalujte MySQL Server:
```
$ sudo apt update
$ sudo apt install mysql-server
```
* Zkontrolujte verzi MySQL Server:
```
$ mysql --version
```
* Pro verzi 8.0.28 nakonfigurujte MySQL Server spuštěním mysql_secure_installation. Nepovolte direktivu pro validaci požadavků na minimální kvalitu hesla
```
$ sudo mysql_secure_installation
```
* Pro verzi 8.0.32 musíte najprve nastavit heslo uživatel root manuálně:
```
$ sudo pkill -f mysql_secure_installation
$ sudo mysql
mysql> alter user 'root'@'localhost' identified with mysql_native_password by 'student';
mysql> quit;
$ sudo mysql_secure_installation
```
* Vytvořte uživatele student a přidělte mu oprávnění
```
$ sudo mysql -u root -p
mysql> create user 'student'@'%' identified by 'student';
mysql> grant all privileges on *.* to 'student'@'%'
```
* Vytvořte databázi 4iz562
* Naimportujte data:
```
$ mysql -u student -p 4iz562 < 4iz562.sql
```
* Nainstalujte Python virtualenv a Jupyter Lab
```
$ sudo apt-get install python3-pip
$ sudo -H pip3 install --upgrade pip
$ sudo -H pip3 install virtualenv
$ mkdir Jupyter
$ cd Jupyter
$ virtualenv environment
$ source environment/bin/activate
$ pip install jupyter
$ pip install jupyterlab
$ pip install mysql-kernel
$ python -m mysql_kernel.install
```
* Přeinstalujte balíček sqlalchemy verzí 1.4.35 (s novější verzí nebude mysql-kernel fungovat)
```
$ pip install sqlalchemy==1.4.35
```
* Spusťte jupyter lab (otevře okno prohlížeče)
```
$ jupyter lab
```
* Otestujte připojení k MySQL:
```
mysql://student:student@localhost:3306
```
* Pokud se objeví následující hláška
```
cryptography' package is required for sha256_password or caching_sha2_password auth methods
```
... nainstalujte z jupyter notebooku cryptography python balíček:
```
!pip install cryptography
```
Pokud následující příkaz nezobrazí seznam databází na mysql serveru, je nejspíš něco špatně s kernelem nebo sqlalchemy balíčkem
```
show databases;
```
Pro diagnostiku problému zkuste nejprve zjistit verze balíčků jupyteru. Z notebooku spusťte následující příkaz:
```
!jupyter --version
```
Výstup by měl být:
```
Selected Jupyter core packages...
IPython          : 8.2.0
ipykernel        : 6.13.0
ipywidgets       : 7.7.0
jupyter_client   : 7.2.2
jupyter_core     : 4.10.0
jupyter_server   : 1.16.0
jupyterlab       : 3.3.4
nbclient         : 0.6.0
nbconvert        : 6.5.0
nbformat         : 5.3.0
notebook         : 6.4.11
qtconsole        : 5.3.0
traitlets        : 5.1.1
```
* Dále zkontrolujte verzi sqlalchemy:
```
!pip show sqlalchemy
```
* Pokud budete instalovat Talend Open Studio for Data Quality, stáhněte zip soubor ze Sourceforge.net a nainstalujte default JDK:
```
$ sudo apt install default-jdk
```

### Docker Container

* Potřebujete mít nainstalovaný git, docker / podman, docker-compose / podman-compose
* Nainstalujte git
```
$ sudo apt install git-all
```
* Nainstalujte docker a docker-compose
```
$ sudo apt install docker docker-compose
```
* Přidejte aktuálního uživatele do skupiny docker
```
$ sudo usermod -aG docker $USER
$ newgrp docker
```
* Otestujte, zda vše funguje
```
$ docker version
$ docker-compose version
```
* Naklonujte si repozitory [4IZ562](https://github.com/dpejcoch/4IZ562)
```
$ git clone https://github.com/dpejcoch/4IZ562
```
* Vytvořte adresář mysql-data na stejné úrovni jako je adresář notebooks
* Přidělte rekurzivně práva ke čtení, zápis a spuštění (pro zjednodušení chmod 777 -R)
* Upravte 4iz562.yml konfigurační soubor pro docker-compose (např. dns)
* Vytvořte kontejnery pomocí:
```
$ docker-compose -f 4iz562.yml up
```
* Na konci výstupu bude link na Jupyter Lab, např.
```
http://127.0.0.1:8888/lab?token=c78357ca766147e337b268f616c531e3d444c1158fd53a0d
```
(token budete mít jiný)
* V Jupyter Labu otevřete MySQL_kernel_intro.ipynb (v adresáři notebooks/W01)
* Připojte se na kontejner s MySQL serverem
```
mysql://student:student@localhost:3306
```
* Zobrazte databáze
```
show databases;
```
* Pokud není na výpisu databáze 4iz562, tak ji vytvořte:
```
create database 4iz562;
```
* Z příkazové řádky z adresáře, ve kterém je sql soubor naimportujte data z SQL (<container id> odpovídá CONTAINER ID **db-server** kontejneru z výpisu docker ps)
```
$ docker exec -i <container id> mysql -ustudent -pstudent 4iz562 < 4iz562.sql
```
* V případě výpisu níže je container id 5ccbd84a7976
```
CONTAINER ID IMAGE COMMAND CREATED STATUS PORTS
5ccbd84a7976 docker.io/library/mysql:8.0.19 --default-authent... 16 minutes ago Up 16 minutes ago 0.0.0.0:3308->3306/tcp, 0.0.0.0:8888->8888/tcp
ee54d46c8a46 localhost/docker_jupyter-lab:latest start-notebook.sh 16 minutes ago Up 16 minutes ago 0.0.0.0:3308->3306/tcp, 0.0.0.0:8888->8888/tcp
```
* Import dat je tedy:
```
$ docker exec -i 5ccbd84a7976 mysql -ustudent -pstudent 4iz562 < 4iz562.sql
```
* V Jupyter Lab budou přístupné notebooky z adresáře notebooks. V případě problémů notebooky číst / ukládat, je nutné na úrovni hosta přidělit příslušná oprávnění
* Kompletní dokumentace docker-compose: [https://docs.docker.com/compose/reference/](https://docs.docker.com/compose/reference/)

