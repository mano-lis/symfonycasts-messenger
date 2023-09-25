# Additional informations for the dockerized version

As some people seemed to have trouble to run the base project, I dockerized the base code so as people can continue to 
learn Symfony with the SymfonyCasts' team amazing work. The original README file is still in the project but has been
renamed. Check it [there](/README_SC.md).
**To use this version, you need to have docker ([install docker](https://docs.docker.com/engine/install/)) and
docker compose ([install docker compose](https://docs.docker.com/compose/install/)) installed.**

## Run the project

1. At the first run, you need to build the containers by running this command:

`docker compose build`

2. Then you can start the containers:

`docker compose up -d`

3. Create the database and run the migration. The .env file is configured to work with PostgreSQL:

```
docker compose exec php bin/console doctrine:database:create
docker compose exec php bin/console make:migration
docker compose exec php bin/console doctrine:migrations:migrate
```

If you encounter problem, then run `docker compose exec php bin/console doctrine:database:drop --force`
and try again the commands below.

4. Compiling the assets:

As mentioned in the original README ([here](/README_SC.md)) you need to have Node and yarn intalled.
Then install the dependencies:

```
yarn install
```

You have to enable a legacy OpenSSL provider by adding an option when compiling the assets. E.g. :

```
NODE_OPTIONS=--openssl-legacy-provider yarn encore dev
```

5. Done! You can check out the site on [https://localhost](https://localhost)

**Following the tuto, don't forget to run any php or symfony command inside your container prefixing it by:**

`docker compose exec php`


