Feature: New family

    Scenario: New family action available
        Given a surname is provided by the User Identitiy
        When the Attach Family page is shown
        Then an "New Family" action is available

        When an active "New Family" action is chosen
        Then a request is made to create a new family and link them to the user

    Scenario: Create new family
        Given a surname is provided by the User Identitiy
        When an request is made to create a new family
        Then the response:
        * Has status 200
        * A new family is represented
        * And the user becomes the Family Admin for the new family

    Scenario: New family action NOT available
        Given a surname is NOT provided by the User Identitiy
        When the Attach Family page is shown
        Then an "New Family" action is visible but is disabled

        When a disabled "New Family" action is hovered over
        Then the following tooltip is displayed
        "A surname must be provided by <users authentication service>"
        
        Given a surname is NOT provided by the User Identitiy
        When a request is made to create a new family
        Then the response:
        * Has status 403
        * Contains the following message: "A surname has not been provided as part of the <users authentication service> user identity. New family not created. Update your <users authentication service> details to include a surname and try again."
