Feature: Weekly Plan

    Scenario: Layout of the plan for a week
        When the plan for a week is displayed
        Then it consists of:
            * a header with the year, week of year
            * a vertical stack of the day rows, starting Monday and ending Sunday
            * each day row consists of a header with the day and month followed by a horizontal stack of time slots for the day
            * each time slot contains a vertical stack of the families tasks for that time slot
            * the task tray

        When the plan for a week becomes visible
        Then it fades in

    Scenario: Show this weeks plan at first
        When the Weekly Plan is first shown after openning the application
        Then the displayed week is the current week

    Scenario: Display of previous and next weeks plans along side the displayed weeks plan
        When the Weekly Plan is shown
        Then the plan for the displayed week is shown in the center

        Given the displayed day is NOT the 1st week of the month previous to the todays month
        When the Weekly Plan is shown
        Then the plan for the previous week is shown to the left of the displayed weeks plan
        And the previous weeks plan is cropped to only show the right hand 15%

        Given the displayed day is NOT the last week of the month following todays month
        When the Weekly Plan is shown
        Then the plan for the next week is shown to the right of the displayed days plan
        And the next weeks plan is cropped to only show the left hand 15%

Feature: Changing the week by clicking

    Scenario: Click pervious weeks plan
        Given the plan for the previous week is visible
        When the plan for the preious week is clicked
        Then the plan for the displayed week scrolls right to become the next weeks plan
        And the previous weeks plan scrolls to the center to become the displayed weeks plan
        And the displayed week becomes the previous week (new previous weeks plan MAY fade in on the left)

    Scenario: Click next weeks plan
        Given the plan for the next week is visible
        When the for the next week is clicked on
        Then the plan for the displayed week scrolls left to become the previous weeks plan
        And the next weeks plan scrolls to the center to become the displayed week plan
        And the displayed week becomes the next week (new next week plan MAY fade in on the right)
 
Feature: Changing the week by swiping

    Scenario: Swipe right
        Given the device supports gestures
        And the plan for the previous week is visible
        When there is a right swipe on the Weekly Plan
        Then the action for clicking on the previous week is performed

    Scenario: Swipe left
        Given the device supports gestures
        And the plan for the next week is visible
        When there is a left swipe on the Weekly Plan
        Then the action for clicking on the next week is performed
