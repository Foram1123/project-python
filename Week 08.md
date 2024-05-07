## Week 08 

# Task 1: Display Menu

Limitation
   •	As of now, the display_menu() function doesn't handle user input or interact with any external services. It's purely for displaying the menu options to the     user. Therefore, limitations regarding data validation or assumptions of external service behaviors are not applicable to this function. 

![screenshot](https://github.com/Foram1123/project-python/blob/main/Images/1display_menu.PNG)

Code: 

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
   
      •	Input: call the main() function.
      •	User Input: Enter 'help' and then 'exit'.
      •	Expected Output: The help menu is displayed initially, and then the application exits without errors.
      •	Actual Output: Verified through manual testing.
      
  #  2.	Test 2: Invalid Command
  
      •	Input: Call the main() function.
      •	User Input: Enter an invalid command.
      •	Expected Output: The application displays an error message indicating that the command is invalid.
      •	Actual Output: Verified through manual testing.

![screenshot](https://github.com/Foram1123/project-python/blob/main/Images/2%20main.PNG)

Code:
   
def main():
    """Main function to prompt the user for commands."""
    display_menu()  # Display the help menu initially

    while True:
        user_input = input("wildlife> ").strip().lower()

        if user_input == 'help':
            display_menu()
        elif user_input == 'exit':
            print("Exiting the application.")
            break
        else:
            print("Error: Invalid command. Please enter 'help' or 'exit'.")


 # Task 3: List Species in City(Stub)  
 
 Limitations:
         •	The search_species(city) function currently acts as a stub and does not interact with a real web service to retrieve species data for a given city. This limitation will be addressed in future iterations of the application when integration with a web service is implemented.

Known Bugs:
         •	There are no known bugs in the implemented functions at the moment.

Test Plan: We will test the new functionality added to the application:

# 1.	Test 1: Display Animal Species in a City

      •	Input: Call the main() function.
      •	User Input: Enter the command "species Cairns".
      •	Expected Output: The application should display a list of species found in the city of Cairns, including their accepted common names and pest status.
      •	Actual Output: Verified through manual testing.
   
# 2.	Test 2: Invalid Command

      •	Input: Call the main() function.
      •	User Input: Enter an invalid command.
      •	Expected Output: The application should display an error message indicating that the command is invalid.
      •	Actual Output: Verified through manual testing.
   
# 3.	Test 3: No Species Found

      •	Input: Call the main() function.
      •	User Input: Enter the command "species UnknownCity".
      •	Expected Output: The application should display a message indicating that no species were found for the specified city.
      •	Actual Output: Verified through manual testing.

![screenshot](https://github.com/Foram1123/project-python/blob/main/Images/3%20species.PNG)

# Errors:



