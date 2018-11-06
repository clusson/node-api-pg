## PostgreSQL - Green IT

## Installation

- App

```bash
git clone git@github.com:clusson/node-api-pg
cd node-api-pg
yarn install
```

- Postgre SQL

_Windows_

```bash
Get PostgreSQL
[postgresql](https://www.postgresql.org/download/windows/)
pg_ctl start
```

_MacOS / Linux_

```bash
brew install postgresql
brew services start postgresql
psql postgres
```

## Database

```sql
CREATE ROLE patrick WITH LOGIN PASSWORD 'password';
ALTER ROLE patrick CREATEDB;
CREATE DATABASE greenit;
GRANT ALL PRIVILEGES ON DATABASE greenit TO patrick;
```

- #### Connection

```bash
psql -d greenit -U patrick
```

- #### Create table

```sql
CREATE EXTENSION IF NOT EXISTS "uuid-ossp";

CREATE TABLE users (
    userId uuid DEFAULT uuid_generate_v4(),
    firstname varchar(25)  NOT NULL,
    lastname varchar(25)   NOT NULL,
    email varchar(50)  NOT NULL,
    created_at date NOT NULL DEFAULT NOW(),
    roleId int NOT NULL,
    PRIMARY KEY (userId),
    FOREIGN KEY (userId) REFERENCES roles(userId)
);

CREATE TABLE roles (
    roleId int NOT NULL,
    role varchar(25)  NOT NULL,
    PRIMARY KEY (roleId)
);

CREATE INDEX "idx_users_email"
ON users ("email");

INSERT INTO users (name, email)
  VALUES ('Johnny', 'Bravo', 'johnny-bravo@contact.me'), ('George Bush', 'george-bush@gov.us');
```

## Launch the app

```bash
node index.js
```

## Commands

- GET: curl http://localhost:3000/users
- POST: curl --data "name=Jerry&email=jerry@example.com" http://localhost:3000/users
- PUT: curl -X PUT -d "name=George" -d "email=george@example.com" http://localhost:3000/users/1
- DELETE: curl -X "DELETE" http://localhost:3000/users/1

social : cron
financier : gain énergétique
