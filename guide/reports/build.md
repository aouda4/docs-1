# Building from Source

## Backend Server

Current system uses postgres as the backend server. In order to correctly run the system, you have to setup postgres database server correctly. Use guide from official [postgres site](https://www.postgresql.org/) to setup the database server. Then use following commands to log into the postgres server and create the local database.

```bash
psql -U postgres
```

Then enter below commands in order to create the role from which the server will access the database. Remember the credentials you entered in this step.

```bash
CREATE ROLE openinventoryuser WITH LOGIN PASSWORD 'password';
CREATE DATABASE openinventorydatabase;
GRANT ALL PRIVILEGES ON DATABASE openinventorydatabase TO openinventoryuser;
\q
```

After this confirm that the database was correctly set-up. Use following commands to log into the system and check the database and user creation.

```bash
psql -U openinventoryuser openinventoryuser
```

The web server uses Node.JS as the backend runtime environment. So you will have to install and configure Node.JS. The backend was tested with [NodeJS 12.16.1 LTS](https://nodejs.org/en/). Install [npm](https://www.npmjs.com/get-npm) to download and install packages for the system. This can be done via following commands in arch-based systems. On windows systems, go to the official websites and download and install the setups.

```bash
sudo pacman -S nodejs-lts-erbium
sudo pacman -S npm
```

Then download the project via github. Use `npm` to install the necessary packages.

```bash
git clone https://github.com/openinventoryorg/backend-api
cd backend-api
npm install
```

Then create new file named `.env`. Put the following content into the file. Put relevant dabase credentials into the file.

```text
PORT=8000
NODE_ENV=development
DATABASE_URL=postgres://openinventoryuser:password@localhost:5432/openinventorydatabase
SALT_ROUNDS=10
JWT_SECRET=jwtsecret
LOG_LEVEL=info
MAIL_SENDER=openinventorysystem@gmail.com
ETHEREAL_USERNAME=maynard64@ethereal.email
ETHEREAL_PASSWORD=E6NyGYDJCgrCr9QKYN
GMAIL_USERNAME=openinventorysystem@gmail.com
GMAIL_PASSWORD=PASSWORD
SITE_API=http://localhost:3000/web-frontend/#
DB_INIT=true
ADMIN_EMAIL=admin@admin.com
SENDGRID_API_KEY=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
ENABLE_ADMINPANEL=true
```

Then use `npm` to serve the web-server. After initial run set `DB_INIT` as `false` in the `.env` file.

## Frontend Website

You need to have `nodejs` and `npm` properly configured. After configuration, clone the frontend server and install packages.

```bash
git clone https://github.com/openinventoryorg/web-frontend
cd web-frontend
npm install
```

After that, simply run the following command and open [http://localhost:3000](http://localhost:3000) to view the server. The project is configured to access [http://localhost:8000](http://localhost:8000) for the API. So make sure that you are running the web backend as the frontend is run.

```bash
npm start
```

## Mobile Application

First, install [flutter](https://flutter.dev).
Then clone this repository and run using flutter tool.

```bash
git clone https://github.com/openinventorysystem/student-mobile
cd student-mobile
flutter run
```

This has to used alongside the open inventory backend. Point the app to the remote server on the first run.
