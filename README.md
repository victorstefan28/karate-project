# Karate Club Management System

This project aims to create a comprehensive Karate Club Management System using the .NET API for the back end and Next.js for the front end. The system focuses on efficiently managing karate clubs, their coaches, and athletes participating in competitions. The features include athlete achievements, competition results, and an overall ranking system.
## Backend (.NET API)

### Setup
1. Clone the repository: `git clone https://github.com/victorstefan28/net-project`
2. Navigate to the backend folder: `cd dotNet-backend/dotNet-backend`
3. Restore dependencies: `dotnet restore`
4. Update database: `dotnet ef database update`
5. Run the API: `dotnet run`

## Frontend (Next.js)

### Prerequisites
- [Node.js](https://nodejs.org/)
- [npm](https://www.npmjs.com/)

### Setup
1. Navigate to the frontend folder: `cd next-frontend`
2. Install dependencies: `npm install`
3. Run the application: `npm run dev`

### Features
- View club details, coach information, and athlete profiles.
- Manage competitions and view medal achievements.
- Display rankings based on points earned by athletes.

## Database diagram
![image]([documentation/images/database_karate_diagrams.png](https://github.com/omacelaru/dotNet-backend/blob/master/documentation/images/database_karate_diagrams.png))

## How to create Database in SQL Server

- start Docker Desktop
- open Terminal

#### Pull image from Docker Hub and run container
```bash
docker pull mcr.microsoft.com/mssql/server:2022-latest

docker run -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=Database.net.2023" -p 1433:1433 --name sqlserver-db-dotnet --hostname dotnet -d  mcr.microsoft.com/mssql/server:2022-latest

docker exec -it sqlserver-db-dotnet "bash"

/opt/mssql-tools/bin/sqlcmd -S localhost -U SA -P Database.net.2023
```
#### Create Database and User
```sql
CREATE DATABASE Database_Karate;
GO
USE Database_Karate;
GO
CREATE LOGIN db_user WITH PASSWORD = "Database.net.user.2023";
GO
CREATE USER db_user FOR LOGIN db_user
GO
EXEC sp_addrolemember 'db_owner', 'db_user';
GO
QUIT
```
#### Connect to Database in Visual Studio
```
In Visual Studio IDE
Click View 
=> Server Explorer 
=> Add Connection 

Data source:    Microsoft SQL Server 
Server Name:    localhost
Authentication: SQL Server Authentication
User Name:      db_user
Password:       Database.net.user.2023
Encrypt:        False
Database Name:  Database_Karate

Click Test Connection
Click OK
```

![image]([documentation/images/connection-db.png](https://github.com/omacelaru/dotNet-backend/blob/master/documentation/images/connection-db.png))

### Connection String
```
Data Source=localhost;Initial Catalog=Database_Karate;User ID=db_user;Password=Database.net.user.2023;Encrypt=False;MultipleActiveResultSets=True;TrustServerCertificate=True"
```
