---
currentMenu: install-json
---

# Install definition

The install.json holds the initial installation configuration.

This file includes things like the MongoDB host (mongo_host) and MongoDB database name (mongo_dbname)
as well as the token retrieved from the site registration from the manager (token).

After these values are added to the file, the command `composer install-frontender` can be issued.

```json
{
    "mongo_host": "mongodb://user:pass@host",
    "mongo_dbname": "frontender_platform",
    "token": "abcdefg123456789"
}
```

This will do the following:

1. Create the .env file (if already present the install will be canceled as this might override existent data);
2. Verify if the site configuration correctly;
3. Create a default site team;
4. Add all managers to the default site team;
5. Download and install core controls.
