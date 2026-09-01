# API Reference: Create Task Endpoint

## Endpoint Information
| Property | Value |
|----------|-------|
| **HTTP Method** | `POST` |
| **Endpoint Path** | `/api/v1/projects/{projectId}/tasks` |
| **Authentication** | Required (Bearer Token) |
| **Content Type** | `application/json` |

---

## Description
Creates a new task within a specified project. The authenticated user becomes the task creator and can assign the task to any valid project member. The task requires a title, due date, and priority level. Description and assignee are optional fields. If no assignee is provided, the task remains unassigned. If no description is provided, the description field is set to an empty string.

---

## Request Parameters

### Path Parameters
| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `projectId` | `string` (UUID) | **Required** | The unique identifier of the project where the task will be created. Must be a valid UUID v4 format. |

### Query Parameters
*This endpoint does not accept query parameters.*

### Request Body Parameters (JSON)
| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `title` | `string` | **Required** | The task title. Must be between 1 and 200 characters. |
| `description` | `string` | Optional | Detailed description of the task. Max 1000 characters. Defaults to empty string if omitted. |
| `assigneeId` | `string` (UUID) | Optional | User ID of the person assigned to this task. Must be a valid user who is a member of the project. If omitted, the task is unassigned (null). |
| `dueDate` | `string` (ISO 8601) | **Required** | The due date in YYYY-MM-DD format. Must be today's date or a future date. |
| `priority` | `string` | **Required** | Priority level of the task. Must be one of: `low`, `medium`, `high`. |

---

## Request Headers
| Header | Value | Required | Description |
|--------|-------|----------|-------------|
| `Authorization` | `Bearer {accessToken}` | **Required** | Valid JWT access token for authenticated user. The user must have permission to create tasks in the specified project. |
| `Content-Type` | `application/json` | **Required** | Indicates the request body format. Must be JSON. |

---

## Response Codes

| Status Code | Description |
|-------------|-------------|
| **201 Created** | Task successfully created. Returns the newly created task object in the response body. |
| **400 Bad Request** | Request validation failed. Possible reasons: missing required fields, invalid date format (not YYYY-MM-DD), due date in the past, invalid priority value, title exceeds 200 characters, or description exceeds 1000 characters. |
| **401 Unauthorized** | Missing or invalid authentication token. The Authorization header is either missing or the token has expired. |
| **403 Forbidden** | Valid authentication token but the user lacks permission to create tasks in the specified project. The user may not be a member of the project. |
| **404 Not Found** | The specified `projectId` does not exist in the system. The project ID may be invalid or deleted. |
| **409 Conflict** | A task with the exact same title already exists in the same project. This prevents duplicate task titles. |
| **429 Too Many Requests** | Rate limit exceeded. The user has made too many requests in a short period. |
| **500 Internal Server Error** | An unexpected error occurred on the server side. The request could not be processed due to a server issue. |

---

## Example Request

### Full Request
