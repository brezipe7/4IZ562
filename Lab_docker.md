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
