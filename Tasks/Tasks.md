Feature: Task properties

    Scenario: Setting the properties of a task
        When a task is created and updated
        Then the value of the following properties can be set:
        * Name
        * Start year/week of year
        * Number of weeks
        * Number of times a week
        * Appointment?
        * Appointment - day of week (Monday through Sunday)
        * Appointment - start time
        * Appointment - duration

        When a task is flagged as an appointment
        Then a day of week, start time and duration must be defined
        And the the Number of times a week is 1

    Scenario: New task
        When a new task is to be created
        Then a modal is openned that captures the properties
        And the modal has Save and Cancel actions

    Scenario: Update task
        When a task is to be updated
        Then a modal is openned that allows the properties to be editted
        And the modal has Save and Cancel actions

    Scenrio: Save properties
        Given a new task is due to be created
        When the Save action is triggered
        Then the a new task is created
        And the provided property values are returned when the state of the task is queried

        Given a task is being updated
        When the Save action is triggered
        Then the updated property values are returned when the state of the task is queried
