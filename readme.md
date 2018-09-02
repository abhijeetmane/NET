# Project Title

API returns list of Books with details

# Project Description

This Project is about creating API in .NET Core 2 to serve list of books and it's details
Project authorization is based on Auth0 authorization services.

### Tech

Application uses a number of projects to work properly:

* [Auth0]
* [.NET Core]
* [C#]

### Running the project

1. Run the project from Visual Studio 2017 or by typing dotnet run in a command window
2. Try to access API using curl command
```
curl -D - http://localhost:5000/api/books
```
This should return a 401 HTTP status code (Unauthorized)
3. Make a POST request like the following
```
curl -X POST -H 'content-type: application/json' -d '{
    "client_id": "YOUR_CLIENT_ID",
    "client_secret": "YOUR_CLIENT_SECRET",
    "audience": "YOUR_AUDIENCE,
    "grant_type":"client_credentials"
}' https://parksite.eu.auth0.com/oauth/token

```
It returns a JSON object like the following:
```
{
    "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsImtpZCI6IlEwRXhOamMzUXpCRE9VSkZSRVJCUTBNME1UY3dRekl6TkRkQ1F6WTVRVGMzUXpBNFJrUkVOZyJ9.eyJpc3MiOiJodHRwczovL2FuZHljaGlhcmUuZXUuYXV0aDAuY29tLyIsInN1YiI6InFBUjBjckRGTWhXdTI2T2hmU2M5eTNIQ2pzU1RBUEdNQGNsaWVudHMiLCJhdWQiOiJodHRwOi8vbG9jYWxob3N0OjYzOTM5LyIsImlhdCI6MTUxNjE3MTA5MywiZXhwIjoxNTE2MjU3NDkzLCJhenAiOiJxQVIwY3JERk1oV3UyNk9oZlNjOXkzSENqc1NUQVBHTSIsInNjb3BlIjoicHJvZmlsZSBvcGVuaWQiLCJndHkiOiJjbGllbnQtY3JlZGVudGlhbHMifQ.eyT7tEJluAz3Pb1h64kgvYtGpmi81BFBB5UvsirPfkoCtOzJNgMFmH-nk8kTi5n_IxQH3GexJM5qUdlvvfSc5QY_-fZ0JHX7tCYfBVf0xTtWz5gyiSgIkk8HMfBQqh2juQLWcxVImz79LmCULzDa5j3uYgyBYiPPr0vv5-gRjfMmuLtvpQu329oL8-7FXS2Bun6t7q6MSSL7jfTp_yRIF4T3cOTvtK6n9KtP7854Gks00ecnIbIqdmD_IoYYDGoxzxCAYFU5mI7TjjtP5avMy-uKoz05fR-XIsMsYJJYin3xgsMqk15aybwuJy1wOHJcLPS3J4kCKmP-XgVSEAxDgA",
    "expires_in": 86400,
    "token_type": "Bearer"
}
```
4.The following GET request
Save $ACCESS_TOKEN received from previous response to $ACCESS_TOKEN variable in cmd line and then make below request
```
curl -H 'Authorization: Bearer '$ACCESS_TOKEN -D - http://localhost:5000/api/books
```
5. Returns the following response:
```
[
	    {
	        "author": "Ray Bradbury",
	        "title": "Fahrenheit 451",
			"ageRestriction": false
	    },
	    {
	        "author": "Gabriel García Márquez",
	        "title": "One Hundred years of Solitude",
			"ageRestriction": false
	    },
	    {
	        "author": "George Orwell",
	        "title": "1984",
			"ageRestriction": false
	    },
	    {
	        "author": "Anais Nin",
	        "title": "Delta of Venus",
			"ageRestriction": true
	    }
]
```