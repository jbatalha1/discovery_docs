# discovery_docs
Project Documentation for Discovery Trademarks

## Authentication

### Authentication via JWT
To authenticate via JWT you must first obtain a JWT. To do so send a POST request to "_open/auth"
containing username and password JSON-encoded like so:
```json
{
  "username":"root",
  "password":"rootPassword"
}
```
Upon success the endpoint will return a 200 OK and an answer containing the JWT in a JSON- encoded object like so:
```json
{
  "jwt":"eyJhbGciOiJIUzI1NiI..x6EfI",
  "must_change_password":false
}
```
This JWT should then be used within the Authorization HTTP header in subsequent requests:
```
Authorization: bearer eyJhbGciOiJIUzI1NiI..x6EfI
```
**__Please note that the JWT will expire after 1 month and needs to be updated.__**
