## Script: Calculate Total Used Database Space in SQL Server (All Databases)

**Description**:
This script calculates the total space used (in GB) by all database files (data and log) across all databases on the SQL Server instance. It queries `sys.master_files` to retrieve the allocated size of each file and aggregates the result.

**Formula**:
- `size * 8.0` = KB (each page is 8 KB)
- Divided by 1024 × 1024 to convert KB to GB

**Use Case**:
- Estimate storage usage across the instance
- Perform storage audits before backup planning or migrations
- Quickly see how much space SQL Server databases are consuming

**Requirements**:
- SQL Server 2005 or later
- Permissions: View access to `master.sys.master_files` (requires `VIEW SERVER STATE` for full instance coverage)

**Notes**:
- The result includes system databases.
- To exclude them, filter out `database_id <= 4` if needed.
