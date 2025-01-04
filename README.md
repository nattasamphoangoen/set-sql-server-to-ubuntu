# set-sql-server-to-ubuntu

## set-sql-server-to-ubuntu
```bash
// check lsb-release (version)
lsb_release -a
-- Distributor ID:	Ubuntu
-- Description:	Ubuntu 24.04.1 LTS
-- Release:	24.04

// install sql server
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
curl https://packages.microsoft.com/config/ubuntu/22.04/prod.list | sudo tee /etc/apt/sources.list.d/mssql-release.list
sudo apt-get update

// install sql server
sudo apt-get install -y mssql-server

// install docker
sudo apt-get install docker.io

// start sql server
sudo docker pull mcr.microsoft.com/mssql/server
sudo docker run -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=123456*x' -p 1433:1433 --name sql_server_container -d mcr.microsoft.com/mssql/server

// run docker
sudo docker ps


// stop container docker (if not want to run)
sudo docker stop sql_server_container

// start container docker (if stop container can't connect to sql server)
sudo docker start sql_server_container

-- connect to sql server
sqlcmd -S localhost -U sa -P 123456*x
-- string connectionString = "Server=localhost,1433;Database=GJITSERVICE;User Id=sa;Password=123456*x;Trusted_Connection=False;MultipleActiveResultSets=true;TrustServerCertificate=True;";


// if can't download
sudo apt-get update
sudo rm /etc/apt/sources.list.d/mssql-release.list
curl https://packages.microsoft.com/config/ubuntu/22.04/prod.list | sudo tee /etc/apt/sources.list.d/mssql-release.list
sudo apt-get update

```


# set change lenguage of ubuntu 24.04
```bash
// open terminal
gsettings set org.gnome.desktop.wm.keybindings switch-input-source "['<Shift>Alt_L']"
```
