# 4IZ562 Řízení kvality dat

## Zadání úlohy

### Audit kvality dat
* Technický profiling
* Validace vybraných atributů pomocí regulárních výrazů, kontrolních součtů, lookup a business pravidel
* Parsing adresy, standardizace, vytvoření porovnávacích kódů a zřetězení na adresní registr
* Root-cause analýza zjištěných defektů
* Odevzdání vypracované zprávy auditora

### Implementace doporučených opatření
* Optimalizace datového modelu
* Nastavení příznaku doručitelnosti na adresu na základě pravidel
* Unifikace dat klientů, adres, kontaktů
* Deduplikace klientů
* Odevzdání CSV souborů

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
* Nakonfigurujte MySQL Server:
```
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
$ jupyter lab
```
### Docker Container


