# Unhandled Error in Express.js Route Handler

This repository demonstrates a common error in Express.js route handlers: the lack of proper error handling for invalid or unexpected input.  Specifically, the `/users/:id` route attempts to parse the `userId` parameter as an integer without checking for potential errors (like non-numeric input). This can lead to unexpected behavior or crashes.

## Bug

The `bug.js` file contains the faulty code.  The route handler directly attempts to parse the `userId` parameter to an integer and uses it to look up a user in the `users` array without any checks if the conversion to an integer is valid. If an invalid parameter is passed (e.g., a string or a special character), a runtime error might occur.

## Solution

The `bugSolution.js` file provides a corrected version.  It includes error handling to check if `userId` is a valid number before attempting to parse it. If it is not a number, the route will return a 400 Bad Request status code.  If a user is not found, it returns a 404 Not Found status code.  This ensures the application gracefully handles invalid input and provides appropriate responses to the client.

## How to Reproduce

1. Clone this repository.
2. Run `npm install express` to install the required dependencies.
3. Run `node bug.js`. 
4. Test with a valid ID (e.g., `/users/1`) and an invalid ID (e.g., `/users/abc`). The first should work, while the second might throw an error in the original code, while the fix will handle this case elegantly.

