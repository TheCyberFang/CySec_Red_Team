# API Testing

---

## API test actions 

Each test is comprised of test actions. These are the individual actions a test needs to take per API test flow. For each API request, the test would need to take the following actions: 

1. Verify correct HTTP status code. For example, creating a resource should return 201 CREATED and unpermitted requests should return 403 FORBIDDEN, etc.

2. Verify response payload. Check valid JSON body and correct field names, types, and values — including in error responses.

3. Verify response headers. HTTP server headers have implications on both security and performance.

4. Verify correct application state. This is optional and applies mainly to manual testing, or when a UI or another interface can be easily inspected.  

5. Verify basic performance sanity. If an operation was completed successfully but took an unreasonable amount of time, the test fails.

---

## Test scenario categories

Our test cases fall into the following general test scenario groups:

    Basic positive tests (happy paths)

    Extended positive testing with optional parameters 

    Negative testing with valid input

    Negative testing with invalid input 

    Destructive testing 

    Security, authorization, and permission tests (which are out of the scope of this post) 

Happy path tests check basic functionality and the acceptance criteria of the API. We later extend positive tests to include optional parameters and extra functionality. The next group of tests is negative testing where we expect the application to gracefully handle problem scenarios with both valid user input (for example, trying to add an existing username) and invalid user input (trying to add a username which is null). Destructive testing is a deeper form of negative testing where we intentionally attempt to break the API to check its robustness (for example, sending a huge payload body in an attempt to overflow the system).   

---

## Test flows

Let’s distinguish between three kinds of test flows which comprise our test plan:

1. Testing requests in isolation – Executing a single API request and checking the response accordingly. Such basic tests are the minimal building blocks we should start with, and there’s no reason to continue testing if these tests fail.

2. Multi-step workflow with several requests – Testing a series of requests which are common user actions, since some requests can rely on other ones. For example, we execute a POST request that creates a resource and returns an auto-generated identifier in its response. We then use this identifier to check if this resource is present in the list of elements received by a GET request. Then we use a PATCH endpoint to update new data, and we again invoke a GET request to validate the new data. Finally, we DELETE that resource and use GET again to verify it no longer exists.

3. Combined API and web UI tests – This is mostly relevant to manual testing, where we want to ensure data integrity and consistency between the UI and API.

We execute requests via the API and verify the actions through the web app UI and vice versa. The purpose of these integrity test flows is to ensure that although the resources are affected via different mechanisms the system still maintains expected integrity and consistent flow.    

---

An API example and a test matrix 

We can now express everything as a matrix that can be used to write a detailed test plan (for test automation or manual tests). 

Let’s assume a subset of our API is the /users endpoint, which includes the following API calls: 
|-------|-----------|-----------|
|   API |   Call    |   Action  |
|--------|-----------|------------|
| GET | /users | List all users | 
| GET | /users?name={username} | Get user by username |
| GET | /users/{id} |	Get user by ID |
| GET | /users/{id}/configurations | Get all configurations for user |
| POST | /users/{id}/configurations | Create a new configuration for user |
| DELETE | /users/{id}/configurations/{id} | Delete configuration for user |
| PATCH | /users/{id}/configuration/{id} | Update configuration for user |

Where {id} is a UUID, and all GET endpoints allow optional query parameters filter, sort, skip and limit for filtering, sorting, and pagination. 