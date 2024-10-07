
# PostgreSQL Backup and Restore Automation on Windows

This guide provides instructions to automate the PostgreSQL backup and restore process using a `.bat` script on Windows. The workflow reads configurations from an `.env` file and uses the `pg_dump` and `pg_restore` tools to perform these operations.

## Supported PostgreSQL Versions
This script is compatible with the following PostgreSQL versions:
- PostgreSQL 9.4 and above

For more details, refer to the [PostgreSQL Documentation](https://www.postgresql.org/docs/).

## Prerequisites
1. **PostgreSQL** installed on your Windows machine (version 9.4 or later).
2. **Environment Variables Configuration** in a `.env` file.
3. **pg_dump** and **pg_restore** executables available (usually found in the PostgreSQL installation directory).

## File Structure
Ensure you have the following files in the same directory:

```
backup_restore.bat  # Batch script to run the backup and restore workflow
.env                # Configuration file with database and path settings
```

## Step 1: Create the `.env` File
Create a `.env` file in the same directory as `backup_restore.bat` with the following content:

```ini
# .env - Configuration File

# PostgreSQL Connection Configuration
PGHOST=localhost
PGPORT=5432
PGUSER=postgres
PGPASSWORD=your_password

# Database Names
DATABASE=mydb
NEW_DATABASE=restored_db

# Parallel Jobs for Backup and Restore
PARALLEL_JOBS=4

# Path to pg_dump and pg_restore executables
PGDUMP_PATH=C:\Program Files\PostgreSQL\11\bin\pg_dump.exe
PGRESTORE_PATH=C:\Program Files\PostgreSQL\11\bin\pg_restore.exe

# Backup Directory Path
BACKUP_PATH=.ackup\mydb_backup
```

### Explanation of `.env` Parameters
- **`PGHOST`**: Hostname of the PostgreSQL server (default: `localhost` for local server).
- **`PGPORT`**: Port number on which PostgreSQL is running (default: `5432`).
- **`PGUSER`**: Username for the PostgreSQL instance.
- **`PGPASSWORD`**: Password for the PostgreSQL user.
- **`DATABASE`**: Name of the source database to backup.
- **`NEW_DATABASE`**: Name of the new database to restore the backup to.
- **`PARALLEL_JOBS`**: Number of parallel processes for `pg_dump` and `pg_restore`. A higher number can speed up the process but consumes more resources.
- **`PGDUMP_PATH`**: Full path to the `pg_dump.exe` executable.
- **`PGRESTORE_PATH`**: Full path to the `pg_restore.exe` executable.
- **`BACKUP_PATH`**: Directory where the backup will be stored.

## Step 2: Create the `backup_restore.bat` File
Create a `backup_restore.bat` file in the same directory with the following content:

```batch
@echo off
setlocal enabledelayedexpansion

:: Read configurations from the .env file
for /f "tokens=* delims=" %%i in (.env) do (
    set "line=%%i"
    setlocal enabledelayedexpansion
    if "!line:~0,1!" neq "#" (
        set "name=!line:*=!"
        set "value=!line:*==!"
        set "%name%=!value!"
    )
)

:: Display configurations
echo Host: %PGHOST%
echo Port: %PGPORT%
echo User: %PGUSER%
echo Database: %DATABASE%
echo New Database: %NEW_DATABASE%
echo Parallel Jobs: %PARALLEL_JOBS%
echo Backup Path: %BACKUP_PATH%

:: Create backup directory if it doesn't exist
if not exist "%BACKUP_PATH%" mkdir "%BACKUP_PATH%"

:: Perform the database backup using pg_dump
echo Performing backup...
"%PGDUMP_PATH%" -U %PGUSER% -h %PGHOST% -p %PGPORT% -d %DATABASE% -F d -j %PARALLEL_JOBS% -f "%BACKUP_PATH%"
if %ERRORLEVEL% neq 0 (
    echo Backup failed!
    exit /b 1
)
echo Backup completed successfully!

:: Create a new database if it does not exist
echo Creating new database %NEW_DATABASE%...
psql -U %PGUSER% -h %PGHOST% -p %PGPORT% -c "CREATE DATABASE %NEW_DATABASE%;"
if %ERRORLEVEL% neq 0 (
    echo Database creation failed!
    exit /b 1
)
echo New database created successfully!

:: Restore the backup to the new database using pg_restore
echo Restoring backup to new database %NEW_DATABASE%...
"%PGRESTORE_PATH%" -U %PGUSER% -h %PGHOST% -p %PGPORT% -d %NEW_DATABASE% -j %PARALLEL_JOBS% "%BACKUP_PATH%"
if %ERRORLEVEL% neq 0 (
    echo Restore failed!
    exit /b 1
)
echo Restore completed successfully!

:: End message
echo PostgreSQL Backup and Restore Workflow completed!
pause
```

### Explanation of `.bat` Script
1. **Read `.env` Configurations**: The script reads each line from the `.env` file and sets the environment variables.
2. **Display Configuration**: Outputs the configuration values for verification.
3. **Create Backup Directory**: Creates the backup directory if it does not exist.
4. **Database Backup with `pg_dump`**: Backs up the specified database using `pg_dump` with the configured parallel jobs.
5. **Create New Database**: Uses `psql` to create the new database.
6. **Restore with `pg_restore`**: Restores the backup to the new database using `pg_restore`.
7. **Error Handling**: Checks the `ERRORLEVEL` after each command to handle errors and exit if any command fails.

## Step 3: Run the Script
1. Open `Command Prompt` on Windows.
2. Navigate to the folder containing `backup_restore.bat` and `.env`.
3. Run the following command:

```batch
backup_restore.bat
```

### Troubleshooting
- **pg_dump or pg_restore Not Found**: Check that the paths in `.env` are correct and point to the actual PostgreSQL executable files.
- **Permissions Error**: Ensure that the PostgreSQL user has the necessary permissions to perform backup and restore operations.
- **Database Connection Issues**: Verify that the `PGHOST`, `PGPORT`, and `PGUSER` values are correct.

## Further Reading
- [PostgreSQL Documentation: Backup and Restore](https://www.postgresql.org/docs/current/backup.html)
- [GitHub Actions Documentation](https://docs.github.com/en/actions)

## Download the Files
Click the link below to download the markdown guide:

- [Download PostgreSQL Backup and Restore Guide](sandbox:/mnt/data/postgresql_backup_restore_guide.md)
