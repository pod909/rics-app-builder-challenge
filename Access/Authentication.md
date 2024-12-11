Background:

    Examples:
        | a supported authentication service |
        | --- | 
        | Google |
        | Apple |
        | Facebook |
        | GitHub |
        | Okta |


Feature: Unkonwn user

    Scenario: Attempted access by an unknown user
        Given the user is NOT authenticated
        When the UI is shown
        Then the user to the unknown user page

    Scenario Outline: Contents of the unknown user page
        When the unknown user page is shown
        Then it provides options to sign-in or sign-up via <a supported authentication service>


Feature: Sign-up

    Scenario Outline: Initiate eign-up
        When a user selects <a supported authenticaiton service> in order to sign up
        Then a request is made to <a supported authenticaiton service> to grant use of the user identity provided by that service
        And the user is presented with the UI provided by <a supported authenticaiton service> in order to achieve this

    Scenario Outline: User identity access granted
        When permission to use the user identity is granted by <a supported authenticaiton service>
        Then the user is connected with the authenticaiton service and the user identitiy
        And the user is redirrected to the URI then where attempting to access as an unauthenticated user


Feature: Sign in

    Scenario: Authentication request
        When a user selects <a supported authentication service> in order to sign in
        Then a request is made to <a supported authenticaiton service> to authenticate the user
        
        When authentication is complete
        Then the UI is refreshed
