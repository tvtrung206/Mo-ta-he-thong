
# PostgreSQL Backup and Restore Workflow Documentation

This documentation provides a step-by-step guide for setting up a GitHub Actions workflow to backup and restore a PostgreSQL database using `pg_dump` and `pg_restore`. The workflow supports configuration of paths, parallel processes, and secure password management using GitHub Secrets.

## Workflow File: `backup_restore.yml`

### Workflow Configuration
```yaml
name: PostgreSQL Backup and Restore

on:
  workflow_dispatch:
    inputs:
      backup-path:
        description: 'Path to save the backup file'
        required: true
        default: './backup'
      pgdump-path:
        description: 'Path to pg_dump executable'
        required: true
        default: 'C:\Program Files\PostgreSQL\11\bin\pg_dump.exe'
      pgrestore-path:
        description: 'Path to pg_restore executable'
        required: true
        default: 'C:\Program Files\PostgreSQL\11\bin\pg_restore.exe'
      database:
        description: 'Name of the source database to backup'
        required: true
        default: 'mydb'
      new-database:
        description: 'Name of the new database to restore the backup to'
        required: true
        default: 'restored_db'
      parallel-jobs:
        description: 'Number of parallel jobs for pg_dump'
        required: true
        default: 4

jobs:
  backup-and-restore:
    runs-on: windows-latest

    env:
      PGPASSWORD: ${{ secrets.PGPASSWORD }}

    steps:
      - name: Set up working directory
        run: mkdir -p ${{ github.event.inputs['backup-path'] }}

      - name: Perform Backup with pg_dump
        run: |
          ${{ github.event.inputs['pgdump-path'] }} -U postgres -h localhost -p 5432 -d ${{ github.event.inputs['database'] }} -F d -j ${{ github.event.inputs['parallel-jobs'] }} -f "${{ github.event.inputs['backup-path'] }}"
        env:
          PGPASSWORD: ${{ secrets.PGPASSWORD }}

      - name: Create New Database
        run: |
          createdb -U postgres -h localhost -p 5432 ${{ github.event.inputs['new-database'] }}
        env:
          PGPASSWORD: ${{ secrets.PGPASSWORD }}

      - name: Restore Backup with pg_restore
        run: |
          ${{ github.event.inputs['pgrestore-path'] }} -U postgres -h localhost -p 5432 -d ${{ github.event.inputs['new-database'] }} -j ${{ github.event.inputs['parallel-jobs'] }} "${{ github.event.inputs['backup-path'] }}"
        env:
          PGPASSWORD: ${{ secrets.PGPASSWORD }}

      - name: Verify the Restore
        run: |
          psql -U postgres -h localhost -p 5432 -d ${{ github.event.inputs['new-database'] }} -c "\dt"
        env:
          PGPASSWORD: ${{ secrets.PGPASSWORD }}
```

## Parameters Explanation

- **`backup-path`**: Specifies the path where the backup files will be stored.
- **`pgdump-path`**: Path to the `pg_dump` executable. Ensure this path is accurate for your PostgreSQL installation.
- **`pgrestore-path`**: Path to the `pg_restore` executable.
- **`database`**: Name of the source database that will be backed up.
- **`new-database`**: Name of the new database to restore the backup to.
- **`parallel-jobs`**: Number of parallel processes to be used for `pg_dump` and `pg_restore`. Higher values speed up the backup and restore process but consume more system resources.

### Using `pg_dump` with Options
The following table shows common `pg_dump` options:

| Option         | Description                                                                                  |
|----------------|----------------------------------------------------------------------------------------------|
| `-U`           | Username for the PostgreSQL instance (e.g., `-U postgres`).                                   |
| `-h`           | Hostname of the PostgreSQL instance (e.g., `-h localhost`).                                   |
| `-p`           | Port number (default is `5432`).                                                              |
| `-d`           | Name of the database to be backed up (e.g., `-d mydb`).                                       |
| `-F`           | Format of the backup file (`c` for custom, `d` for directory).                                |
| `-j`           | Number of parallel jobs (e.g., `-j 4`).                                                       |
| `-f`           | Path to save the output file (e.g., `-f /path/to/backup`).                                     |

### Using `pg_restore` with Options
The following table shows common `pg_restore` options:

| Option         | Description                                                                                  |
|----------------|----------------------------------------------------------------------------------------------|
| `-U`           | Username for the PostgreSQL instance.                                                        |
| `-h`           | Hostname of the PostgreSQL instance.                                                         |
| `-p`           | Port number.                                                                                 |
| `-d`           | Name of the database to restore to.                                                          |
| `-j`           | Number of parallel jobs for restoring (e.g., `-j 4`).                                        |
| `-F`           | Format of the backup file (same format used in `pg_dump`).                                    |

### Recommendations for Parallel Processes (`-j`)
- **System Resources**: Before setting the number of parallel jobs, consider your system's resources:
  - **CPU**: If you have 8 CPU cores, use `-j 4` or `-j 8` for optimal performance.
  - **RAM**: Make sure your system has sufficient RAM for handling parallel processes.
- **Recommended Settings**:
  - **4 Cores, 16 GB RAM**: Use `-j 2` to `-j 4`.
  - **8 Cores, 32 GB RAM**: Use `-j 4` to `-j 8`.
  - **16 Cores, 64 GB RAM**: Use `-j 8` to `-j 16`.
  - **For High-End Servers**: You can increase `-j` up to the number of logical CPUs available, but test to avoid overloading.

## Example Scenarios
1. **Basic Backup with 2 Parallel Processes**:
    ```bash
    pg_dump -U postgres -h localhost -p 5432 -d mydb -F d -j 2 -f "/backups/mydb_backup"
    ```

2. **Restore Using 4 Parallel Processes**:
    ```bash
    pg_restore -U postgres -h localhost -p 5432 -d newdb -j 4 "/backups/mydb_backup"
    ```

3. **Full Workflow Command**:
    This command runs the entire workflow with 4 parallel jobs for both backup and restore:
    ```bash
    pg_dump -U postgres -h localhost -p 5432 -d mydb -F d -j 4 -f "/backups/mydb_backup"
    createdb -U postgres -h localhost -p 5432 newdb
    pg_restore -U postgres -h localhost -p 5432 -d newdb -j 4 "/backups/mydb_backup"
    ```

## Setting Up GitHub Secrets
To store the PostgreSQL password securely:
1. Go to `Settings` > `Secrets` > `Actions`.
2. Add a new secret with the name `PGPASSWORD` and set its value to your PostgreSQL password.

### Important Notes
- Ensure that `pg_dump` and `pg_restore` paths are correctly set in your workflow.
- Adjust parallel jobs (`-j`) based on your system's capabilities to avoid overloading.

For more information, refer to the official [PostgreSQL documentation](https://www.postgresql.org/docs/).
