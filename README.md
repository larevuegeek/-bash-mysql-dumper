# Bash Mysql Dumper

Un simple script Bash commenté en français pour sauvegarder vos bases de données MySQL ou Mariadb quotidiennement

## Pour installer le script

Vous avez juste à placer le script dans le répertoire de votre choix, par exemple votre répertoire /home

```sh
cd /home/XXXX/
git clone https://github.com/larevuegeek/bash-mysql-dumper.git
```

Ensuite, il faut rendre le script executable

```sh
cd bash-mysql-dumper
chmod +x mysql-dumper.sh
```

Enfin, remplacez les varables BACKUP_USER et BACKUP_PASSWORD par les valeurs correspondants à votre systèmes

```sh
BACKUP_USER="UTILISATEUR"
BACKUP_PASSWORD="MOTDEPASSE"
```

## Pour executer le scripts
```sh
cd /home/xxxx/bash-mysql-dumper/
sudo ./mysql-dumper.sh
```

## Options Disponibles

| Option | Description | Valeur attendu |
| ------ | ------ | ------ |
| BACKUP_DIR | Emplacement de la sauvegarde | Chemin système |
| BACKUP_EXPIRATION_DAYS | Délai de conservation des sauvegarde en jours | Chiffre |
| BACKUP_CMD | Commande Mysql ou Mariadb | mysql ou mariadb |
| BACKUP_CMD_DUMP | Commande Mysqldump ou Mariadb-dump | mysqldump ou mariadb-dump |
| BACKUP_CMD_ADM | Commande Mysqladmin ou Mariadb-admin | mysqladmin ou mariadb-admin |
| MODE | MODE 1 = un fichier par base / MODE 2 = 1 fichier par table | Chiffre |
| VERBOSE | Active ou désactive la verbosité | Y ou N |
| GZIP_COMPRESSION | Active la compression GZIP | Y ou N |
| ADD_DROP_DATABASE | Ajoute l'option --drop-database | Y ou N |
| ADD_DROP_TABLE | Ajoute l'option --drop-table | Y ou N |

## Programmation quotidienne

Vous pouvez programmer la sauvegarde automatique quotidienne via un cron.
Voici un exemple pour un cron tous les jours à 3h00 du matin :

```sh
crontab -e

00 03  * * *   root    /home/xxxx/bash-mysql-dumper/mysql-dumper.sh
```