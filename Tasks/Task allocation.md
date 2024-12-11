Featue: Task trey

    Scenario: Unplanned tasks
        When the Weekly planner is shown
        Then the task trey contains the none-appointment tasks that should occur that week
        But that have not been fully allocated to the plan

        Given a task needs to happen more than once
        When the task is shown in the Task Trey
        Then a badge shows the number of times the number of times the task should occur minus the number of times it has been allocated to the plan being displayed

Feature: Auto planning of appointments

    Scenario: Appointments automatically added to the plan
        When a weekly plan is shown
        Then a task allocation is automatically created for the appointments that occur that week
        And are not included in the Task Trey

Feature: Planning of tasks

    Scenrio: Moving tasks from the Task Trey
        Given a task is not an appointment
        When a task is dragged from the Task Trey to a time slot for a given day of the week
        Then a task allocation is created linking the task to the weekly plan

    Scenario: Reallocation of tasks
        Given a task is not an appointment
        When the allocation of a task is dragged to a new time slot
        Then the allocation is moved to the new timeslot

Feature: Allocating the task to a user
    Scenario: Short click on a task allocattion
        When a task allocation is clicked on
        Then a memeber of the family to be linked with the task allocation via a modal

Feature: Updating a task
    Scenario: Long click on a task allocation
        When there is a long click on a task allocation
        Then the values of a task can be updated

    Scenario: Long click on a task
        When there is a long click on a task in the Task Trey
        Then the values of the task can be updated

    Scenario: To many allocations of an updated task
        When the number of times a task occurs is changed
        Then the allocations for the task are deleted
        