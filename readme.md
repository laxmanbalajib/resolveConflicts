# Starting the Project

Run the following:

```bash
docker-compose -f ./docker-compose-dev.yml up db
```

in the parent directory to bring up the database. Then, at a new prompt, run:

```bash
npm i
```

This installs all the components required to run the API. Afterwards, run:

```bash
npm run dev
```

This will start the API for the database.

# A Note on User Roles

The facility table includes a column named permissions. The number in a user's permissions column corresponds to the following sets of permissions (this may change as the application scales):

* 0x0xx0: xx === 00 is regular user; 01 is manager; 10 is admin; 11 is undefined at this point.
	* Valid roles:
		* 0x0000 (0) is regular dash user.
		* 0x0001 (1) is regular torch user.
		* 0x0010 (2) is manager dash user.
		* 0x0011 (3) is manager torch user.
		* 0x0100 (4) is admin dash user.
		* 0x0101 (5) is admin torch user.
	* Invalid roles:
		* 0x0110 (6).
		* 0x0111 (7).
    * 0x1000 (8).
    * 0x1001 (9).
    * 0x1010 (10).
    * 0x1011 (11).
    * 0x1100 (12).
    * 0x1101 (13).
    * 0x1110 (14).
    * 0x1111 (15).

# Routes

## POST

* /categories_and_criteria/ : Returns payload containing data for the categories and criteria tables.

* /criteria_ids/ : Returns payload of the different criterias.

* /login/ (requires and email and password JSON payload in body) : Returns a JSON payload with a valid token to send to the protected GET routes listed below. Token belongs in header as a Bearer token when sending GET requests to protected routes.

* /update_password/ (requires an email and new password JSON payload in body as well as a valid Bearer token in the request header) : This changes the password of a given user.

* /password_reset/ (requires the email of the account you want to change, as well as being logged in as admin) : This generates a random, ten-digit password for a given user, updates the user's password, and sends the new password back to the person running the request. Must be logged in as admin.

* /hospitals/ (requires a unique email that isn't in the hospital table, as well as standard credentials) : This will allow you to update or create a new user. If admin, you can create a new user by passing an email that isn't in use. If you pass an email under key "accountToModify" in use as admin, it will update the user with the corresponding id. If you run this as a non-admin user, sans-accountToModify, then you will update your own hospital information. Available fields are accountToModify, name, address, state, zipcode, type, rural, city, numBeds, email and torchMember.

* /inputs/ : This version of the route requires you to pass accountToDisplay in the body of your request as admin. This allows you to query for inputs for a different hospital if you are admin, and intended to be used to fill the admin's dashboard view.

## GET (Requires login)

* /inputs/ : Returns payload of inputs for the current quarter.

* /inputs/?year=20XX&quarter=Y, XX = year, Y = quarter from 1 - 4 : Returns payload of inputs for a given month.

* /inputs/?yearBegin=20WW&quarterBegin=X&yearEnd=20YY&quarterEnd=Z with WW and YY = year, and X and Z = quarter : Returns payload of inputs between a given range of quarters.





* /hospitals/ (requires being logged in as the admin account) : Returns payload of basic hospital data sans-admin.

* /population/ (requires queries for parameter: CAH, PPS, Rural, NonRural; as well as quarter and year) : Will return all inputs in a given quarter and year for a given parameter.

app.post('/categories_and_criteria', categoriesAndCriteria);
app.post('/criteria_ids', criterias);
app.post('/facilities_list', facilitiesList);
app.post('/population', populationRoute);
app.post('/target', inputsTargetRoute);
app.post('/inputs', inputsHandler);
app.post('/facilities', facilitiesPost);
app.post('/login', login);
app.post('/update_password', updatePassword);
app.post('/password_reset', passwordReset);
app.post('/add_user', addUser);
app.post('/remove_user', removeFacility);
app.post('/export_data', exportData);
