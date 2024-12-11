Feature: List existing families

    Scenario: List similar families based on user identitiy surname
        Given a surname is provided by the User Identity
        When the Attach Family page is shown
        Then a list of families with a similar surname is shown

    Scenario: No surename provided by the user identity
        Given NO surname is provided by the User Identity
        When the Attach Family page is shown
        Then a empty list of families is shown
        And the user can enter a surname to search for families on

    Scenarion: Families listed
        When the list of families is shown
        Them list is sorted by similarity (most similar at the top)
        And the the following details are provided for each family:
            * Surname
            * Family admin user id
            * Family admin picture
        And the user can change the surname to search on

    Scenario: Family list pagingation
        When the list of families has more then 20 entries
        Then the list is paginated
        And the first, up to 3 previous, current, up to 5 next, and last page can be accessed dirrectly
        And dirrect access to each page is only provided once
        
        When there is a gap in the list of pages that can be accessed dirrectly
        Then this is shown using an elipsis

    Scenario: Search for a different family
        When the surname to search on is changed
        Then the list of families is updated

    Scenario: No surname provided
        When NO surname is provided to search on OR only one character is provided
        Then the list of families is empty


Feature: Attach existing family

    Scenario: Attach a family from the list of existing families
        When a family is selected from the list of existing families
        Then the users details are updated to link them to the selected family
        