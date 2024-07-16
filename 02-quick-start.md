# 02. Quick Start

This guide explains how to get started with the Technical Writer Tasks API using **Postman**.

Take the following steps to authenticate and run your first API request for creating a technical writer task:

1. Visit [our website](), click **Register**, and follow the instructions. You will receive an email containing the **API key** to the address you used for registration. Copy the API key: you'll need it in Step 6.

2. In Postman, create a new **POST** request.

3. Paste the following URL:

    ```http
    https://api.techwriter.xyz/task
    ```
4. Navigate to the **Authorization** tab under your request URL. In the **Auth Type** drop-down menu, select **API Key**.

5. Enter `x-api-key` in the **Key** field.

6. Enter your API key (obtained in Step 1) in the **Value** field.

7. Make sure that the **Add to** option is set to **Header**.

8. In the **Body** tab, select **raw** and **JSON** and paste the following:

    ```json
    {
      "title": "My First Task",
      "component": "API_DOCS"
    }
    ```
9. Click **SEND** to run the request. The API will return the details of the task you've just created:

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
- Visit the API specification: [Technical Writer Tasks API Specification](05-open-api-spec.yaml).