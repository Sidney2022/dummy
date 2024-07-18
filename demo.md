
# Description
Develop an endpoint to handle requests to create a subscription plan and also subscription plan features.  it is only open to super admin. If the data is deleted successfully, it will be returned to the client with a '202' status. If an error occurs, an appropriate error status will be returned.
[link](https://dbdiagram.io/d/66969e458b4bb5230e807920)
# Acceptance Criteria
The endpoint deletes a blog post data.
The endpoint can be called only by a super admin.
Returns a 202 status code and the correct response body when blog is deleted successfully.
Returns a 404 status code and the correct response body when blog is not found.
Returns a 403 status code and the correct response body when a user that is not an admin tries to access the endpoint.
Returns an appropriate error message when an error occurs.
Requirements
 Implement API endpoint for deleting blog posts.
 Confirm deletion action to prevent accidental deletions.
 Make sure the endpoint can only be called by a super admin
 Ensure blog post safely deleted in the database.
 Handle unexpected errors and return the appropriate status code.
Expected Outcome
Super Admin should be able to send a request to the backend to delete a blog post, with data temporarily removed and confirmation provided.
Endpoints
[DELETE] /api/v1/blogs/:id

Description: Delete a Blog Data.

Path Parameters:

id: The of the blog to be deleted. Default is 1.
Success Response:

Status: 202 OK

Body:

{
"message": "Blog successfully deleted",
"status_code": 202
}
Error Response:

Status: 500 Internal Server Error

Body:

{
    "message": "Internal server error.",
    "status_code": 500,
}
Unauthorized User Response:

Status: 403 Forbidden

Body:

{
    "message": "You are not authorized to perform this action",
    "status_code": 403,
}
Unauthorized User Response:

Status: 404 Not Found

Body:

{
    "message": "Blog with the given Id does not exist",
    "status_code": 404,
}
Invalid Method Response:

Status: 405 Method Not Allowed

Body:

{
    "message": "This method is not allowed.",
    "status_code": 405,
}
Bad Request Response:

Status: 400 Bad Request

Body:

{
    "message": "An invalid request was sent.",
    "status_code": 400,
}
Testing
Test Scenarios

Successful Deletion of Blog Post

Ensure that the endpoint successfully deletes a blog post.
Confirm that the status code is 202.
No Blog Post Found

Simulate a scenario where no blog posts are present in the database.
Confirm that the status code is 404.
Confirm that the response body contains an appropriate message.
Insufficient Permission

Simulate a scenario where an ordinary user wants to access this endpoint.
Confirm that the status code is 403.
Confirm that the response body contains an appropriate message.
Internal Server Error

Simulate an internal server error to raise an exception.
Verify that the endpoint returns a 500 Internal Server Error status code.
Confirm that the response body contains an appropriate error message.
Invalid Id Parameters

Send requests with invalid id parameters (e.g., non existing obect Id).
Verify that the endpoint returns a 400 Bad Request status code.
Confirm that the response body contains an appropriate error message.
Invalid Method

Send a request using an invalid HTTP method (e.g., POST) to the endpoint.
Verify that the endpoint returns a 405 Method Not Allowed status code.
