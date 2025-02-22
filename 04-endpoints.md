# Endpoints

## Overview

## GET List Tasks

### URL and Description

```
https://api.techwriter.xyz/task/tasks
```
This endpoint returns details of all technical writer tasks.

### Authentication

To authenticate your request, pass the as `X-API-Key` in the request header. Learn more: [Authentication](03-authentication.md).

### Query Parameters

Optionally, you can add the following query parameters in any combination to filter the results:

- `status`: `OPEN` / `IN_PROGRESS` / `COMPLETED`  
  Filters by status of the task: **open**, **in progress**, or **complete**. In the current version, you can update the task status manually using our website. Later we'll add an endpoint allowing to update tasks including their statuses.

- `component`: `API_DOCS` / `HELP_CENTER` / `SDK_DOCS` / `OAS_FILE`  
  Filters by documentation type.

- `updatedAfter`  
  Filter tasks that have been updated after a specific date (YYYY-MM-DD).

### Responses

On success, the API will return a list of all tasks with detailed information:

```json
[
  {
    "task_id": "2",
    "title": "API Quick Start",
    "description": "Create a quick start guide for the Technical Writer Tasks API.",
    "status": "OPEN",
    "component": "API_DOCS",
    "connected_tasks": [
      {
        "task_id": "1",
        "title": "Update the API Spec",
        "description": "Identify gaps in the Technical Writer Tasks API Specification and update it.",
        "status": "OPEN"
      }
    ]
  }
]
```

If your request is unauthorized or the API key is missing or invalid, the API will return a 401 error:

```json
{
 "message": "Unauthorized, API key missing or invalid.",
 "code": "401"
}
```

## POST Add a New Task

### URL and Description

```
https://api.techwriter.xyz/task
```
This endpoint returns details of all technical writer tasks.

### Authentication

To authenticate your request, pass the as `X-API-Key` in the request header. Learn more: [Authentication](03-authentication.md).

### Request Body

In the request body, specify the following:

- `title`  
  (required) The task title.

- `description`  
  The task description.

- `component`:  `API_DOCS` / `HELP_CENTER` / `SDK_DOCS` / `OAS_FILE` 
  (required) The documentation type to update.

- `connnected_tasks`  
  An array of connected tasks, identified by ID. To retrieve the ID of the task you wish to connect, use [GET List tasks](#get-list-tasks).

```json
{
  "title": "Update the API Spec",
  "description": "Identify gaps in the Technical Writer Tasks API Specification and update it.",
  "component": "API_DOCS",
  "connected_tasks": [
    "1"
  ]
}
```

### JS Example

Here is a JS example for running this endpoint:

```js
const options = {
  method: 'POST',
  headers: {
    accept: 'application/json',
    'content-type': 'application/json',
    'X-API-Key': 'YOUR_API_KEY'
  },
  body: JSON.stringify({
      "title": "Update the API Spec",
      "description": "Identify gaps in the Technical Writer Tasks API Specification and update it.",
      "component": "API_DOCS",
      "connected_tasks": [
        "1"
      ]
  })
};


fetch('https://api.techwriter.xyz/task', options)
  .then(response => response.json())
  .then(response => console.log(response))
  .catch(err => console.error(err));
```

### Responses

On success, the API will return the details of task you've just created. Note that an ID will be assigned to your task automatically, and the `status` will be `OPEN` by default.

```json
{
  "task_id": "2",
  "title": "API Quick Start",
  "description": "Create a quick start guide for the Technical Writer Tasks API.",
  "status": "OPEN",
  "component": "API_DOCS",
  "connected_tasks": [
    {
      "task_id": "1",
      "title": "Update the API Spec",
      "description": "Identify gaps in the Technical Writer Tasks API Specification and update it.",
      "status": "OPEN"
    }
  ]
}
```

If your request is unauthorized or the API key is missing or invalid, the API will return a 401 error:

```json
{
 "message": "Unauthorized, API key missing or invalid.",
 "code": "401"
}
```
