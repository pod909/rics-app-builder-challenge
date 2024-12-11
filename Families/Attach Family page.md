Feature: Attach Family page

    Scenario: Display the Attach Family page
        Given the user is authenticated
        And access to the User Idtentity has been granted
        And the user has NOT been linked with a family
        When the UI is displayed
        Then the Attach Family page is shown
