# Creating a Postgres Database and Loading a File using Docker

## Step 1: Run a Postgres Container

Run a Postgres container with a specified name, environment variables, port mapping, and data volume.

```console
docker run --name postgresql \
    -e POSTGRES_USER=postgres \
    -e POSTGRES_PASSWORD=postgres \
    -p 5432:5432 \
    -v f:\guides\docker-guide\postgres\data:/var/lib/postgresql/data \
    -d postgres:14.7
```

Note:

- Use --name to specify the container name.
- Set POSTGRES_USER and POSTGRES_PASSWORD environment variables for authentication.
- Map port 5432 on the host machine to the same port inside the container using -p.
- Mount a data volume from the local file system to persist data.

## Step 2: Create a Database

Use pgAdmin or psql to create a new database named fastlight2.

### Using pgAdmin

Open pgAdmin, right-click on Databases, and select "New Database". Fill in the details as follows:

| Field | Value | | --- | --- | | Name | fastlight2 | | Owner | postgres |

Click "Save" to create the new database.

### Using psql (Alternative)

Alternatively, use the command line with psql to create the database. Open a Command Prompt or PowerShell and navigate to your working directory.

```console
psql -d postgres -U postgres -c 'CREATE DATABASE fastlight2;'
```

## Step 3: Add an Extension

Add the extension pg_trgm using psql in the fastlight2 database.

```console
psql -d fastlight2 -U postgres -c 'CREATE EXTENSION IF NOT EXISTS pg_trgm;'
```

## Step 4: Load a File into Postgres

Load a SQL script into your newly created fastlight2 database using psql.

```console
psql -d fastlight2 -U postgres -f .\fastlight2_day1.sql
```

Note:

- Change directory (cd) to the location of your SQL file.
- Run the above command to load the script into Postgres.

Improvements made include:

- Adding headings and subheadings for better readability and organization.
- Using Markdown syntax for headers, bold text, and code blocks.
- Providing clear instructions and notes where necessary.
- Updating environment variables in the docker run command.
- Correcting a typo in the Postgres version number.
- Adding whitespace to make the code more readable.