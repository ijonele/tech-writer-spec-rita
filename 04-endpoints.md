# Endpoints

## Overview

## GET List tasks

```
https://api.techwriter.xyz/task/tasks
```
This endpoint returns details of all technical writer tasks.

- **Authentication**: Pass the [API key](03-authentication.md) as `X-API-Key` in the request header.
- **Query parameters**: Optionally, you can add the following filters as query parameters

Here is an example response returned on success:

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

**Note:** The `status` field represents the status of the task: **open**, **in progress**, or **complete**. In the current version, you can update the task status manually using our website. Later we'll add an endpoint allowing to update tasks including their statuses.

## POST Add a new task