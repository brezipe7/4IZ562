# 4IZ562 Řízení kvality dat
(Aktualizováno pro LS 2024/25)

## Struktura kurzu

### Úvod do řízení dat

1. 2025-02-21: Úvod, organizační pokyny, motivace k řešení problematiky datové kvality, co je to kvalita dat a informací. Konfigurace labu, představení umělých dat, výstupů, MySQL toolbox.
2. 2025-02-28: Data, Data Management, vlastnosti dat, příčiny a důsledky nekvalitních dat, Six Sigma, Kaizen, rekonciliace dat, root-cause analýza. Případové studie, měření vlastností da, měření nákladů nekvalitních dat.
3. 2022-03-07: Data Governance, související právní normy, Entity Recognition, kvalita metadat, datové katalogy, Data Lineage a Data Provenance. Právní normy relevantní pro naši praktickou úlohu, návrh principů, standardů, politik v praxi. Entity Recognition v praxi, anonymizace, masking, pseudonymizace dat.

### Analýza současného stavu

4. 2025-03-14: Data Profiling a alternativní přístupy (analýza procesů, testování kontrol), Data Drift. Výstupy profilingu, příklady implementace v různých nástrojích, process mining.
5. 2025-03-21: Validace dat, definice pravidel, datové kontroly, DQ Firewall, validační služby, vazba na metriky výkonnosti řízení dat. Validace v praxi, validace proti vybraným API.
6. 2025-03-28: Audit kvality dat. Vypracování zprávy auditora.

### Implementace nápravných opatření
7. 2025-04-04: Parsing, standardizace, unifikace. Standardizace a unifikace v praxi. Prevence vzniku chyb, oprava stávajících chyb: standardizace, korekce, implementace kontrol. Proces řízení kvality dat (metodiky, modely, projekt implementace).
8. 2025-04-11: *Inovační týden (výuka odpadá)* **Termín odevzdání zprávy auditora**
9. 2025-04-18: *Good Friday (výuka odpadá)*
10. 2025-04-25: Imputace chybějících pozorování, obohacování dat o externí datové zdroje, geocoding.
11. 2025-05-02: *Děkanský den (výuka odpadá)*
12. 2025-05-09: Porovnávání a slučování záznamů, Master Data Management, Householding.

### Monitorování datové kvality

13. 2025-05-16: Implementace monitoringu, kontinuální zvyšování kvality dat, Augmented Data Quality, specifické formy datové kvality (nestrukturovaná data, Linked Data, ...). Extrakce metadat z nestrukturovaných dat, deduplikace nestrukturovaných dat. Aktuální trendy a výzvy. Příprava na test. 

### Zkouškové období

* 19.5. - 27.6. **zkouškový test**, **odevzdání nápravných opatření** (alespoň týden před koncem)

## Zkouškový test

* 10 otázek z teorie po 4 bodech, celkem 40% celkového hodnocení

## Praktická úloha

* 60% celkového hodnocení

### Audit kvality dat
1. Technický profiling: s pomocí vybraného nástroje vytvořte profilaci dat (základní popisné statistiky, četnosti syntaktických vzorů, ...)
2. Validace vybraných atributů pomocí regulárních výrazů, kontrolních součtů, lookup a business pravidel
3. Spočtěte úroveň kvantitativních vlastností dat (správnost, úplnost, konzistentnost, ...)
4. Root-cause analýza zjištěných defektů
5. Na příkladu modelové firmy odhadněte roční výši nákladů na nekvalitní data
6. Porovnejte možné přínosy nápravných opatření se souvisejícími náklady
7. Proveďte prioritizaci nápravných opatření
8. Navrhněte externí datové zroje pro obohacení dat
9. Navrhněte strategii pro doplnění chybějících hodnot
10. Odevzdání vypracované zprávy auditora + naměřené charakteristiky / náklady (PDF dokument dle šablony pro zprávu auditora)

### Implementace doporučených opatření
1. Optimalizace datového modelu
2. Parsing adresy, standardizace, vytvoření porovnávacích kódů a zřetězení na adresní registr
3. Nastavení příznaku doručitelnosti na adresu na základě pravidel
4. Doplnění chybějících pozorování
5. Unifikace dat klientů, adres, kontaktů
6. Deduplikace klientů
7. Návhr kontrol bránících dalšímu vzniku chyb v datech
8. Odevzdání CSV souborů s vyčištěnými daty + PDF dokumentace provedených opatření

## Celková klasifikace

* 60% bodů lze získat z praktické úlohy
* 40% bodů lze získat z testu
* bonusové body z quizů na přednáškách
* bonusové body za inovativní přístup

* 90 a více bodů = 1
* 75 - 89 bodů = 2
* 60 - 74 bodů = 3
* 50 - 59 bodů = 4+ (možnost dozkoušení)
* 0 - 49 bodů = nevyhověl

## Zdroje ke studiu

* Prezentace k přednáškám
* Články výslovně zmíněné přednášejícím
* McGILVRAY, D. Executing Data Quality Projects: Ten Steps to Quality Data and Trusted Information. Morgan Kaufmann, 2008. xviii, 325 s. ISBN 978-0-12-374369-5.
* MAYDANCHIK, Arkady. Data quality assessment. Bradley Beach: Technics Publications, LLC, [2007], ©2007. xiv, 321 stran. Data quality for practitioners series. ISBN 978-0-9771400-2-2.
* CHAPMAN, P., KHABAZA, T., SHEARER, C.: CRISP-DM 1.0 Step by step data mining guide. IBM, 2012. ftp://ftp.software.ibm.com/software/analytics/spss/support/Modeler/Documentation/14/UserManual/CRISP-DM.pdf
* Materiály dostupné na www.dataquality.cz
* PEJČOCH, D. Metody řešení problematiky neúplných dat [online]. 2011-01-13 Přednáška č. 4 v rámci Data Quality Tutorial. Dostupné pod odkazem: https://github.com/dpejcoch/4IZ562/tree/master/papers/Data_Imputation.pdf.
* PEJČOCH, D. Benchmark přístupů k Fuzzy Match / Merge. Sborník prací účastníků vědeckého semináře doktorského studia. Fakulta informatiky a statistiky VŠE. Praha 2009. ISBN 978-80-245-1524-3.
* LOSHIN, D. The Practitioner’s Guide to Data Quality Improvement. Burlington: Morgan Kaufmann as inprint of Elsevier, 2011. ISBN 978-0-12-373717-5.
* ENGLISH,  Larry P. Improving Data Warehouse and Business Information Quality: Methods for Reducing Costs and Increasing Profits. Wiley & Sons, 1999. xxvi, 518 s. ISBN-10 0-471-25383-9.
* LEE, Yang W., PIPINO, Leo L., FUNK, James D., WANG, Richard Y. Journey to Data Quality. The MIT Press, 2006. 240 s. ISBN-10 02-621-2287-1.
* BATINI, Carlo, SCANNAPIECO, Monica. Data Quality: Concepts, Methodologies and Techniques. Berlin: Springer-Verlag, 2006. xix, 262 s. ISBN-10 3-540-33172-7.
* BERSON, Alex, DUBOV, Larry. Master Data Management and Customer Data Integration for a Global Enterprise. McGraw-Hill Companies, 2007. xxi, 393 s. ISBN-10 0-07-226349-0.
* DYCHÉ,  Jill, LEVY, Evan. Customer data integration: Reaching a Single Version of the Truth. SAS Institute Inc., Wiley & Sons, 2006, xxiv, 294 s. ISBN-10 0-471-91697-8.
* REDMAN, T. Data Quality: The Field Guide. Boston: Butterworth-Heinemann MA, 2001. xviii, 241. ISBN-10 1-55558-251-6.
* DAMA International: The DAMA Guide to the Data Management Body of Knowledge (DAMA-DMBOK). Technics Publication, LLC, 2009. ISBN 978-1-9355040-2-3.
* Chaudhuri S., Ganjam K., Ganti V., Motwani R.: Robust and Efficient Fuzzy Match for Online Data Cleaning, SIGMOD 2003, June 9-12, 2003 San Diego, CA.
* D'Ambrosio A. Boosted Incremental Tree-based Imputation of Missing Data, PhD. thesis, Universitá degli Studi di Napoli Federico II. 2007.
* PEJČOCH, D. Audit datové kvality podle IT Assurance Guide: Using COBIT - 1. díl. In: Data Quality CZ [online]. 2012-03-07 07:14:52. Dostupné z: [URL].
* PEJČOCH, D. Audit datové kvality podle IT Assurance Guide: Using COBIT - 2. díl. In: Data Quality CZ [online]. 2012-03-07 07:14:52. Dostupné z: [URL].
* PEJČOCH, D. Audit datové kvality podle IT Assurance Guide: Using COBIT - 3. díl. In: Data Quality CZ [online]. 2012-03-07 07:14:52. Dostupné z: [URL].

## Lab

Pro vypracování semestrální práce potřebujete data modelové firmy dostupné jako SQL dump z MySQL / MariaDB databáze. SQL soubor chráněný heslem je dostupný z adresáře [data](data/4iz562.zip).

Doporučené nástroje pro vypracování semestrální práce: MySQL Server, Python + Jupyter Lab, Talend Open Studio for Data Quality [https://sourceforge.net/projects/talendprofiler/](https://sourceforge.net/projects/talendprofiler/)

Alternativní postupy pro vytvoření experimentálního prostředí jsou shrnuty v následujících odstavcích: 

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

