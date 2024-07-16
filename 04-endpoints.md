# Endpoints

## Overview

## GET List tasks

```
https://api.techwriter.xyz/task/tasks
```
This endpoint returns details of all technical writer tasks. Optionally, you can filter them using query parameters.

- **API spec**: [GET List tasks](06-open-api-spec.yaml#getTasks)
- **Authentication**: Pass the [API key](03-authentication.md) as `X-API-Key` in the request header.
- **Query parameters**: Optionally, you can add the following filters as query parameters


A short description
HTTP method and URI
Required headers, including authentication
Request body structure (for POST) - note that it is missing from the specification file so you can use your imagination and experience here 🙂
Success and error response examples
Status codes explanation
Python or JS code examples - how to authenticate and make a request only to the POST endpoint

## POST Add a new task