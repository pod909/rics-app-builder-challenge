Feature: Daily Plan

    Scenario: Layout of the plan for a day
        When the plan for a day is displayed
        Then it consists of:
            * a header with the date of the day
            * a vertical stack of the days time slots
            * each time slot containing a vertical stack of the families tasks for that time slot
        And the users tasks are displayed with a saturated version of the tasks colours
        And the other tasks are displayed with a faded version of the tasks colours

        When the plan for a day becomes visible
        Then it fades in

    Scenario: Show todays plan at first
        When the Daily Plan is first shown after openning the application
        Then the displayed day is today

    Scenario: Display of previous and next day plans along side the displayed days plan
        When the Daily Plan is shown
        Then the plan for the displayed day is shown in the center

        Given the displayed day is NOT the 1st day of the month previous to the todays month
        When the Daily Plan is shown
        Then the plan for the previous day is shown to the left of the displayed days plan
        And the previous days plan is cropped to only show the right hand 15%

        Given the displayed day is NOT the last day of the month following todays month
        When the Daily Plan is shown
        Then the plan for the next day is shown to the right of the displayed days plan
        And the next days plan is cropped to only show the left hand 15%

Feature: Changing the day by clicking

    Scenario: Click pervious days plan
        Given the plan for the previous day is visible
        When the plan for the preious day is clicked
        Then the plan for the displayed day scrolls right to become the next days plan
        And the previous days plan scrolls to the center to become the displayed days plan
        And the displayed day becomes the previous day (new previous day plan MAY fade in on the left)

    Scenario: Click next days plan
        Given the plan for the next day is visible
        When the for the next day is clicked on
        Then the plan for the displayed day scrolls left to become the previous days plan
        And the next days plan scrolls to the center to become the displayed days plan
        And the displayed day becomes the next day (new next day plan MAY fade in on the right)
 
Feature: Changing the day by swiping

    Scenario: Swipe right
        Given the device supports gestures
        And the plan for the previous day is visible
        When there is a right swipe on the Daily Plan
        Then the action for clicking on the previous day is performed

    Scenario: Swipe left
        Given the device supports gestures
        And the plan for the next day is visible
        When there is a left swipe on the Daily Plan
        Then the action for clicking on the next day is performed
