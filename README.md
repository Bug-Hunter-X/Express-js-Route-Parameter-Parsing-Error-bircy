# Express.js Route Parameter Parsing Error

This repository demonstrates a common error in Express.js applications where route parameters are not properly parsed as integers, leading to unexpected behavior or errors.  The bug involves missing error handling when the route parameter is not a valid integer, potentially causing incorrect data retrieval or unexpected 404 errors.  The solution involves adding robust error handling to ensure that route parameters are correctly parsed and handled.

## Bug

The bug is located in `bug.js`. The route handler does not explicitly check if `req.params.id` is a valid integer before attempting to parse it.  If `req.params.id` is not an integer, `parseInt(userId)` will return `NaN`, causing the `.find()` method to fail and the code to proceed to the `else` block resulting in a 404 error, even if a user exists with an ID that is parsed incorrectly.  For example if user ID is a string "123a" it will return 404.

## Solution

The solution is provided in `bugSolution.js`. It includes error handling by checking if `parseInt(userId)` returns a valid integer. If the parsing fails, it handles this case explicitly and returns an appropriate error message instead of silently proceeding with an invalid value.
