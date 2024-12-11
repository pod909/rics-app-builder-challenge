Feature: Rate limiting

    Scenario: More than 20 authenticated requests a second to the same URI
        Given the request is authenticated
        When the user makes more than 20 requests to the same URI with in a second
        Then authentication is revoked
        And the response:
        - Has HTTP code 429
        - Redirrects to the unknown user page after 1 second
        - Contains the message "We have receied a flood of requests from you. Access has be controlled. Please wait and the log-in page will be displayed shortly."

    Scenario: More than 200 authenticated requests a second to any URI
        Given the request is authenticated
        When the user makes more than 200 requests with in a second
        Then authentication is revoked
        And the response:
        - Has HTTP code 429
        - Redirrects to the unknown user page after 1 second
        - Contains the message "We have receied a flood of requests from you. Access has be controlled. Please wait and the log-in page will be displayed shortly."

    Scenario: More than 2 UNauthenticated requests a second to a URI
        Given the user is NOT authenticated
        When more than 2 requests for a URI are received from the same ip address with in a second
        Then the response:
        - Has HTTP code 429
        - Redirrects to the unknown user page after 1 second
        - Contains the message "We have receied a flood of requests from you. Access has be controlled. Please wait and the log-in page will be displayed shortly."
