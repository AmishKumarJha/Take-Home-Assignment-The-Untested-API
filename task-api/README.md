## Assignment Summary

### Work Completed

- Inspected the existing Express.js Task API and its service, route, and validation layers.
- Added unit tests for the `taskService` covering:
  - Task creation and default values
  - Retrieving all tasks
  - Finding tasks by ID
  - Filtering tasks by status
  - Pagination
  - Updating tasks
  - Removing tasks
  - Completing tasks
  - Task statistics
- Added integration tests using Jest and Supertest for the API routes.
- Tested the happy path for the existing task endpoints.
- Added edge-case tests for validation, missing tasks, invalid inputs, pagination, status filtering, and task assignment.

### New Feature Added

- Added a new `PATCH /tasks/:id/assign` endpoint to assign a task to a user.
- Added an `assignee` field to the assigned task.
- Added validation for the `assignee` field:
  - Missing assignee
  - Empty assignee
  - Whitespace-only assignee
  - Non-string assignee
- Added handling for assigning a task that does not exist.
- Added handling for tasks that are already assigned.
- Added integration tests covering successful assignment and assignment edge cases.

### Bug Fixes

- Fixed the pagination offset bug so that page 1 starts with the first task.
- Fixed the status filtering bug by changing partial matching to exact status matching.
- Discovered an additional issue where completing a task changes its priority to `medium`; this was documented but left unfixed.
- Created `BUG_REPORT.md` documenting the bugs discovered, their root causes, fixes, and the additional unfixed issue.

### Testing and Coverage

- Achieved more than the required 80% test coverage.
- Final test results:
  - **2 test suites passed**
  - **41 tests passed**
  - **0 tests failed**
  - **92.9% statement coverage**
  - **82.75% branch coverage**
  - **93.1% function coverage**
  - **92.19% line coverage**

### Deployment

- Deployed the API to Render and verified the live API using browser requests and Postman.
- Tested the deployed API for task creation, retrieving tasks, statistics, task completion, and task assignment.

### What I'd Test Next

If I had more time, I would add additional tests for invalid pagination parameters, invalid status values, concurrent updates, additional validation scenarios, and the remaining uncovered branches and error-handling paths.

### What Surprised Me

The pagination implementation contained an off-by-one error that caused page 1 to skip the first tasks. I also found that status filtering used `includes()`, which allowed partial values such as `do` to match both `todo` and `done`.

### Questions Before Shipping to Production

Before shipping this API to production, I would ask about database persistence, authentication and authorization, task ownership, assignee management, input validation requirements, and the expected behavior for concurrent updates.

### Links

**Git Repository:**  
https://github.com/AmishKumarJha/Take-Home-Assignment-The-Untested-API

**Live API:**  
https://take-home-assignment-the-untested-api-6iyx.onrender.com