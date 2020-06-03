# gorillamux-postgis-service
Testing out a Postgis database service using Go.

Some basic additional command info.

brew install postgresql
brew services start PostgreSQL - Run now and on restart
brew install postgis

export makes a variable something that will be included in child process environments. It does not affect other already existing environments. In general there isn't a way to set a variable in one terminal and have it automatically appear in another terminal, the environment is established for each process on its own.

Adding it to your .profile makes it so that your environment will be setup to include that new variable each time you log in though. So it's not being exported from one shell to another, but instead is instructing a new shell to include it when it sets up the initial environment.

export APP_DB_USERNAME=postgres
export APP_DB_PASSWORD=postgres
export APP_DB_NAME=postgis

CREATE TABLE products
(
    id SERIAL,
    name TEXT NOT NULL,
    price NUMERIC(10,2) NOT NULL DEFAULT 0.00,
    CONSTRAINT products_pkey PRIMARY KEY (id)
)

docker run -p 5432:5432 --name postgis -e POSTGRES_PASSWORD=postgres -e POSTGRES_USER=postgres  -e POSTGRES_DB=postgis -d postgis/postgis