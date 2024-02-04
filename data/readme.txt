# linea para hacer backup remoto. 
ssh postgres@mininet.exp 'tar -zcvf - *' > mininet.tar.gz
ssh postgres@mininet.exp 'pg_dump database' > database_backup

ssh postgres@mininet.exp 'pg_dump name_of_database' > database_backup
ssh postgres@mininet.exp pg_dump database | zip > database_backup.zip

ssh postgres@mininet.exp create database databaserecovered
ssh postgres@mininet.exp psql database < 2018_03_15-database.backup

--
./neo4j-shell -c dump > /home/user/backup-neo4j.cyp

ssh user@mininet.exp ' /home/other_user/neo4j-community-3.3.2/bin/neo4j-shell -c dump > /home/user/2018_06_12-backup-neo4j'

--
#Para agregar clave en el servidor remoto y poder hacer el backup 
ssh-keygen
ssh-copy-id user@mininet.exp
# ahora no va a pedir más clave al logearme de esa compu

# Logearse a miinet
# .ssh/authorized_keys va a aparecer la clave
# QUEREMOS que el usuario POSTGRES tenga esa clave también.
# para eso;  ser root y

sudo -s

# como root me logueo a postgres

su postgres

#  Agregar esa clave a .ssh/authorized_keys

# si es read only con ls -la puedo quien tiene los permisos sobre ese archivo.
# para cambiarlos

chown postgres:postgres authorized_keys
 
# donde : separa usuario:grupo




--
sudo su - postgres
pg_dump name_of_database > name_of_backup_file
