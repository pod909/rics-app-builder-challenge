Feature: Family Planner page

    Scenario: Display Daily plan in portrait
        Given the user is authenticated
        And the user is linked to a family
        And the orientation of the display is portrait
        When the UI is displayed
        Then the Daily Plan is shown

    Scenario: Display Weekly Plan in landscape
        Given the user is authenticated
        And the user is linked to a family
        And the orientation of the display is landscape
        When the UI is displayed
        Then the Weekly Plan is shown
