# PostgreSQL Installation Guide for Ubuntu

This guide will walk you through the steps to install PostgreSQL on an Ubuntu-based system using the official PostgreSQL APT repository. 

###
![Screenshot from 2025-01-19 09-18-09](https://github.com/user-attachments/assets/e29e0b1c-54bb-4379-b9e7-142dae4d6a41)
###

## Prerequisites

- A system running Ubuntu (any supported version).
- A user account with `sudo` privileges.

## Installation Steps

### 1. Add the PostgreSQL APT Repository

First, install the necessary packages:

```bash
sudo apt update
sudo apt install wget ca-certificates -y
```
- Then, add the PostgreSQL APT repository:

```bash
wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
echo "deb http://apt.postgresql.org/pub/repos/apt/ $(lsb_release -cs)-pgdg main" | sudo tee /etc/apt/sources.list.d/pgdg.list
```
### 2. Update the Package List
Now, update your package list to include the PostgreSQL packages:

```bash
sudo apt update
```
### 3. Install PostgreSQL
- To install the latest stable version of PostgreSQL, run the following command:

```bash
sudo apt -y install postgresql
```
- If you'd like to install a specific version (e.g., PostgreSQL 16), you can use the following:

```bash
sudo apt -y install postgresql-16
```
### 4. Verify Installation
- Once the installation is complete, verify the version of `PostgreSQL` installed:

```bash
psql --version
```
- This should output something like:

```bash
psql (PostgreSQL) 17.2 (Ubuntu 17.2-1.pgdg24.04+1)
```
### 5. Start PostgreSQL Service (if not already running)
- If PostgreSQL is not running, you can start the service with:

```bash
sudo systemctl start postgresql
```
### 6. Enable PostgreSQL to Start on Boot
- To ensure PostgreSQL starts automatically when your system boots, enable the service:

```bash
sudo systemctl enable postgresql
```
### 7. Access the PostgreSQL Shell
- PostgreSQL creates a default administrative user called postgres. To access the PostgreSQL shell as the postgres user, run:

```bash
sudo -i -u postgres
psql
```
- You should see the PostgreSQL prompt:

```bash
postgres=#
```
### 8. Create a New Database and User (Optional)
- You can now create a new database and user with the following commands:

## Create a database:

```sql
CREATE DATABASE mydatabase;
```
## Create a new user:

```sql
CREATE USER myuser WITH PASSWORD 'mypassword';
```
- Grant privileges to the user on the database:

```sql
GRANT ALL PRIVILEGES ON DATABASE mydatabase TO myuser;
```
### 9. Exit PostgreSQL Shell
- To exit the `PostgreSQL` shell, type:

```sql
\q
```
### 10. Clean Up (Optional)
- If you want to remove `PostgreSQL` completely from your system, you can use the following command:

```bash

sudo apt-get --purge remove postgresql*
sudo apt-get autoremove
```
## Troubleshooting
- If you run into any issues during installation, make sure to:

- Double-check the repository URL for your Ubuntu version.
- Ensure your system is up-to-date with sudo apt update.
- For more detailed troubleshooting, you can refer to the https://www.postgresql.org/docs/


# Single-Shot Commands 
```bash
sudo apt update

sudo apt install wget ca-certificates -y

wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -

echo "deb http://apt.postgresql.org/pub/repos/apt/ $(lsb_release -cs)-pgdg main" | sudo tee /etc/apt/sources.list.d/pgdg.list

sudo apt update

sudo apt -y install postgresql

psql --version

sudo systemctl start postgresql

sudo systemctl enable postgresql

sudo -i -u postgres
psql

\q
```
