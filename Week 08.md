## Week 08 

# Task 1: Display Menu

Limitation
   •	As of now, the display_menu() function doesn't handle user input or interact with any external services. It's purely for displaying the menu options to the     user. Therefore, limitations regarding data validation or assumptions of external service behaviors are not applicable to this function. 

![screenshot](https://github.com/Foram1123/project-python/blob/main/Images/1display_menu.PNG)

def display_menu():
    """
    Display the menu options for the application.

    This function prints the menu options available to the user.
    The menu includes commands like 'Display help' and 'Exit the application'.
    """
    print("Help")
    print("====")
    print("The following commands are recognized.")
    print("Print Help Menu")
    print("Exit the Program")

# Task 2: User Input

Limitations:
•	The main() function currently does not handle more complex command inputs or interact with external services. It's designed to handle basic commands like 'help' and 'exit' only.

Known Bugs:
   •	There are no known bugs in the main() function at the moment.
   
Test Plan: We have tested the main() function with the following scenarios:
   # 1.	Test 1: Display Help Menu and Exit
   
      •	Input: Call the main() function.
      •	User Input: Enter 'help' and then 'exit'.
      •	Expected Output: The help menu is displayed initially, and then the application exits without errors.
      •	Actual Output: Verified through manual testing.
  #  2.	Test 2: Invalid Command
  
      •	Input: Call the main() function.
      •	User Input: Enter an invalid command.
      •	Expected Output: The application displays an error message indicating that the command is invalid.
      •	Actual Output: Verified through manual testing.

