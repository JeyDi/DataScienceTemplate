# Info about Database Docker images and containers



### Launch Cointainers with shared folder





## Neo4J Database

Pull docker Neo4J official image

```powershell
docker pull neo4j:latest
```

Run Neo4J Container

https://www.melvinvivas.com/neo4j-in-docker/

```powershell
docker run \
		--name n4jDB \
    --publish=7474:7474 --publish=7687:7687 \
    --env NEO4J_AUTH=neo4j/ve2hrhtv88 \
    --volume=$HOME/neo4j/data:/data \
    --rm -d neo4j
```

Then you have to connect to the Database with the client: http://localhost:7474/browser/

Or you can connect your browser pointing on the DB



## Microsoft SQL Server

Info about microsoft sql server docker image

https://hub.docker.com/_/microsoft-mssql-server

Official Microsoft documentation about Microsoft SQL Server

https://docs.microsoft.com/en-us/sql/linux/quickstart-install-connect-docker?view=sql-server-2017&pivots=cs1-bash

Complete user (not official) guide

https://www.sqlshack.com/backup-and-restore-operations-with-sql-server-2017-on-docker-containers-using-azure-data-studio/



Info abount images

https://hub.docker.com/_/microsoft-mssql-server



WARNINGS: The 2019 sql server version and image doesn't work!!!!



Pull the image for default easy container

```powershell
docker pull mcr.microsoft.com/mssql/server:2017-latest
```



Pull the image for linux (ubuntu) containers

```bash
sudo docker pull mcr.microsoft.com/mssql/server:2019-GA-ubuntu-16.04
```

GA = General Availability (more complex and usefull use)



Run the image on windows with **bash** or Linux, MacOs systems



**Base Launch 2019 version** (not working)

```bash
sudo docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=Ve2hrhtv88!." -p 1433:1433 --name sql1 -d mcr.microsoft.com/mssql/server:2019-GA-ubuntu-16.04
```



**Base Launch 2017 version** (working)

```bash
sudo docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=ve2hrhtv88..' -p 1433:1433 --name sql1 -d mcr.microsoft.com/mssql/server:2017-latest
```



Change the SA Password

```bash
sudo docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd \
   -S localhost -U SA -P "ve2hrhtv88.." \
   -Q 'ALTER LOGIN SA WITH PASSWORD="ve2hrhtv92.."'
```



**Advance Launch** (not working for -v volume problems)

```bash
sudo docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=ve2hrhtv88" \
   --name 'sql1' -p 1401:1433 \
   -v sql1data:/var/opt/mssql \
   -d mcr.microsoft.com/mssql/server:2019-GA-ubuntu-16.04
```



Run the image on windows with **powershell**

```powershell
docker run -e "ACCEPT_EULA=Y" -e "SA_PASSWORD=<YourStrong!Passw0rd>" `
   -p 1433:1433 --name sql1 `
   -d mcr.microsoft.com/mssql/server:2017-latest
```



Using Backup with docker and SQL Server

https://docs.microsoft.com/en-us/sql/linux/tutorial-restore-backup-in-sql-server-container?view=sql-server-ver15

Connect with your client using this info

- Server: localhost
- Username: SA
- Password: <yourstrongpassword>



Put Backup inside the machine

```bash
docker cp ~/DockerShared/volumes/SqlServer/backup/DC.bak sql1:/var/opt/mssql/data/
```



**Launch the SQL Commands Bash inside the running container**

```bash
sudo docker exec -it sql1 "bash"
```

Then launch the sql cmd bash

```bash
/opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P "ve2hrhtv88.."
```

If you put after the string code: -q " query" you launch a specific query into db

