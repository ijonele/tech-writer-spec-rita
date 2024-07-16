# Endpoints

## Overview

## GET List tasks

### URL and description

```
https://api.techwriter.xyz/task/tasks
```
This endpoint returns details of all technical writer tasks.

### Authentication

To authenticate your request, pass the as `X-API-Key` in the request header. Learn more: [Atuthentication](03-authentication.md).

### Query parameters

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

## POST Add a new task

### URL and description

```
https://api.techwriter.xyz/task/task
```
This endpoint returns details of all technical writer tasks.

### Authentication

To authenticate your request, pass the as `X-API-Key` in the request header. Learn more: [Atuthentication](03-authentication.md).

### Request body

In the request body, specify the following:

- `title`  
  (Required)The task title.

- `description`  
  (Optional) The task description.

- `component`:  `API_DOCS` / `HELP_CENTER` / `SDK_DOCS` / `OAS_FILE` 
  (Required) The documentation type to update.

- `connnected_tasks`
  (Optional) An array of connected tasks, identified by ID. To retrieve the ID of the task you wish to connect, use [GET List tasks](#get-list-tasks).

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

### Responses

On success, the API will return the details of task you've just created:

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
