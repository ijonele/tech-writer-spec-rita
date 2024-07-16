# Quick Start

Follow the steps below to authenticate and run your first API request for **creating a technical writer task**.

This guide uses [Postman](https://web.postman.co) for running requests. Before starting, register there if you don't have an account yet.

## Step 1: Get the API key

1. Visit [our website]().
2. Click **Register**, and follow the instructions.
3. You'll receive an email containing the **API key** to the address you used for registration.
4. Copy the API key: you'll need it in Step 3.

## Step 2: Create a request

1. In [Postman](https://web.postman.co), create a new **POST** request.

2. Paste the following URL:

    ```http
    https://api.techwriter.xyz/task
    ```
## Step 3: Authenticate

1. In the **Authorization** tab under your request URL, select **API Key** from the **Auth Type** drop-down menu.

2. Enter `x-api-key` in the **Key** field.

3. Enter your API key (obtained in Step 1) in the **Value** field.

4. Make sure that the **Add to** option is set to **Header**.

## Step 3: Add the request body

1. In the **Body** tab, select **raw** and then **JSON**.

2. Paste the following:

    ```json
    {
      "title": "My First Task",
      "component": "API_DOCS"
    }
    ```
## Step 4: Create your first task

1. Click **SEND** to run the request.

2. The API will return the details of the task you've just created:

    ```json
    {
      "task_id": "1",
      "title": "My First Task",
      "description": "",
      "status": "OPEN",
      "component": "API_DOCS",
      "connected_tasks": []
    }
    ```
## What's next?

- Learn more about the [available endpoints](04-endpoints.md).
- Visit the API specification: [Technical Writer Tasks API Specification](06-open-api-spec.yaml).