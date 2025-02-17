### VirtualBox VM

* Nainstalujte VirtualBox z [https://www.virtualbox.org/](https://www.virtualbox.org/)
* Stáhněte si iso Ubuntu Focal Fosa 20.04 [https://www.releases.ubuntu.com/20.04/](https://www.releases.ubuntu.com/20.04/) ... instalační process ale trvá dlouho
* Prostředí funguje také na Jammy Jellyfish 22.04.1 LTS [https://www.releases.ubuntu.com/22.04/](https://www.releases.ubuntu.com/22.04/) ... celkově svižnější
* V obou případech zvolte variantu nainstalovat (ne live ISO) a minimalistickou instalaci
* S Jammy Jellyfish se nainstaluje Python 3.10 (naše laby předpokládají 3.8.4), ale zatím stávající notebooky spuštěné pod 3.10 varují pouze před budoucím odstranění některých balíčků
* Vytvořte nové VM s alespoň 2 CPU, 8GB RAM a 20-30 GB VDI
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
