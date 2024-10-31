# Authentication with Keycloak and OAuth2 Proxy

Run with:
```
docker-compose up -d
```
(Takes a few seconds for OAuth2 Proxy to resolve Keycloak.)

Add this entry to /etc/hosts:
```
127.0.0.1       keycloak
```

### Keycloak admin console

* Go to http://localhost:8080.
* Login: admin / password
* Select "graph" in the top left drop-down menu to configure the imported graph realm (imports/realm-export.json).
* You can create a new realm with the "Create realm" button at the bototm of the drop-down menu. Note: "Keycloak" is the master realm.

### To test the OAuth2 flow:
- Create a test user in Keycloak:
	- Select "Users" in the left menu.
	- Create a user and enable "Email verified" and set a password in the Credentials tab.
- Go to http://localhost:8089 and log in as the new user.
- OAuth2 Proxy will redirect authenticated requests to the httpbin index page. You can inspect the HTTP response headers to view the authenticated user's info (X-User, X-Email, X-Groups).