# discovery_docs
Project Documentation for Discovery Trademarks

## Authentication

### Authentication via JWT
To authenticate via JWT you must first obtain a JWT. To do so send a POST request to "_open/auth"
containing username and password JSON-encoded like so:
```json
//endpoint example: https://inventa.com/_open/auth
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

## Documents

Documents are grouped into collections. A collection contains zero or more documents. If you are familiar with relational database management systems (RDBMS) then it is safe to compare collections to tables and documents to rows.

### Get one document from a collection

To do so you need make a GET request with the collection name and document id:

```
Endpoint: http://inventa.com/_db/discovery/_api/document/{collection_name}/{document_id}"
```


```shell
shell> curl --header 'accept: application/json' --dump - http://inventa.com/_db/discovery/_api/document/AO/1221191585174",

HTTP/1.1 OK
content-type: application/json; charset=utf-8
etag: "_X1nZXoW--B"
x-content-type-options: nosniff

{ 
  "_key" : "104299", 
  "_id" : "products/104299", 
  "_rev" : "_X1nZXoW--B", 
  "Name" : "Inventa International",
  "JurisdictionIso": "AO"
  ...
}
```
### Get All documents from a collection

There are several ways you can do this. The more performant way is to create a cursor.


