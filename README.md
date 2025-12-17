# API Explorer: Mastering RESTful Connections


A project focusing on understanding and correctly using third-party APIs. This task involves reading API documentation, identifying usable endpoints, authentication methods, request structures, and response formatting. The API chosen for this project is **MoviesDatabase API**.

---

## API Overview

The **MoviesDatabase API** provides detailed information about movies, TV series, actors, and entertainment-related data. It allows developers to search movie titles, retrieve cast information, find similar content, and get metadata such as release dates, ratings, and genres. The API is lightweight, easy to use, and supports structured JSON responses making it ideal for application integration or learning API usage in TypeScript.

---

## API Version

- **Version:** v1

---

##  Available Endpoints

| Endpoint | Description |
|----------|-------------|
| **/titles** | Returns a list of movies or TV titles, supporting filters like year, genre, and sort order. |
| **/titles/{id}** | Retrieves detailed information for a specific title by IMDb ID. |
| **/titles/{id}/cast** | Returns cast information for a specific title. |
| **/titles/search/title?q={query}** | Searches for titles based on search keywords. |
| **/titles/random** | Returns a random movie or TV title. |

---

## Request and Response Format

API requests and responses use **HTTP** with **JSON** format.

###  Example Request
```http GET https://moviesdatabase.example.com/titles/search/title?q=Avatar```

### Example JSON Response

`{
"results": [
{
"id": "tt0499549",
"titleText": "Avatar",
"releaseYear": { "year": 2009 },
"genres": ["Action", "Adventure", "Sci-Fi"]
}
]
}`

### Authentication

To use the MoviesDatabase API, you must authenticate using an API key provided in the request header.

✔️ Required Authentication Header
X-API-KEY: your_api_key_here

✔️ Example Authenticated Request
curl -H "X-API-KEY: your_api_key_here" \
https://moviesdatabase.example.com/titles/random

### ️ Error Handling

When an error occurs, the API will return a standard HTTP status code and a JSON error response.

Status Code	Meaning	How to Fix
* 400 Bad Request	Incorrect request format or missing query.	Check your request syntax and parameters.
* 401 Unauthorized	API key is invalid or missing.	Ensure your key is correct and included in the headers.
* 404 Not Found	Requested ID or endpoint does not exist.	Verify the endpoint or resource ID.
* 429 Too Many Requests	Too many requests in a short time.	Wait or reduce request frequency.
* 500 Server Error	Internal API error.	Try again later.
* 
### ️ Example Error Response
`{
"status": 404,
"message": "Resource not found"
}`

###  Usage Limits and Best Practices

* The API enforces rate limits, meaning you can only make a limited number of requests within a given time period.
* 
* Always cache repeated data (e.g., repeated search results) to reduce the number of API calls.
* 
* Protect your API key: never expose it in public repositories.
* 
* Validate user input before making requests to avoid unnecessary errors.
* 
* Implement proper error handling to ensure your application continues to function even if the API fails.


