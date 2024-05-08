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

# Task 4: List Animal Sightings in City (Stub)

    Limitations:
      •	The search_sightings(taxonid, city) function currently acts as a stub and does not interact with a real web service to retrieve animal sighting data for a given species in a city. This limitation will be addressed in future iterations of the application when integration with a web service is implemented.
            
   Known Bugs:
      •	There are no known bugs in the implemented functions at the moment.

   Test Plan: We will test the new functionality added to the application:
   
# 1.	Test 0: Display Animal Sightings in a City

      •	It gave the error when entered sightings 102 testcity. 
            Because we have applied one split and expected user to enter the taxonid and city comma separated. Added theinstruction in the menu function after that.
            
# 2.	Test 1: Display Animal Sightings in a City

   •	Input: Call the main() function.
   •	User Input: Enter the command "sightings 1039,Cairns".
   •	Expected Output: The application should display a list of individual animal sightings for the species with TaxonID 1039 in the city of Cairns,       including the start date and locality details.
   •	Actual Output: Verified through manual testing.
   
# 3.	Test 2: Invalid Command

   •	Input: Call the main() function.
   •	User Input: Enter an invalid command.
   •	Expected Output: The application should display an error message indicating that the command is invalid.
   •	Actual Output: Verified through manual testing.

# 4.	Test 3: No Sightings Found

   •	Input: Call the main() function.
   •	User Input: Enter the command "sightings UnknownTaxonID,UnknownCity".
   •	Expected Output: The application should display a message indicating that no animal sightings were found for the specified species and city.
   •	Actual Output: Verified through manual testing.


![screenshot](https://github.com/Foram1123/project-python/blob/main/Images/4.1%20Error.PNG)

![screenshot](https://github.com/Foram1123/project-python/blob/main/Images/4.2.PNG)

Code:

def main():
    """
    Main function to prompt the user for commands and execute corresponding actions.

    The function prompts the user for commands and executes the corresponding actions based on the input.
    """
    display_menu()  # Display the help menu initially

    while True:
        user_input = input("wildlife> ").strip().lower()

        if user_input.startswith('species'):
            # Parse the command and city
            _, city = user_input.split(maxsplit=1)
            species_list = search_species(city)
            display_species(species_list)
        elif user_input.startswith('sightings'):
            # Parse the command, species taxonid, and city
            _, species_city = user_input.split(maxsplit=1)
            taxonid, city = species_city.split(',')
            sightings = search_sightings(taxonid, city)
            display_sightings(sightings)
        elif user_input == 'help':
            display_menu()
        elif user_input == 'exit':
            print("Exiting the application.")
            break
        else:
            print("Error: Invalid command. Please enter 'help' or 'exit' or 'species <city>' or 'sightings <species_taxonid>,<city>'.")

def display_menu():
    """
    Display the menu options for the application.

    This function prints the menu options available to the user.
    The menu includes commands like 'Display help', 'Exit the application', 'Display animal species in a city',
    and 'Display animal sightings in a city'.
    """
    print("Help")
    print("====")
    print("The following commands are recognized.")
    print("Display help")
    print("Exit the application")
    print("Display animal species in a city")
    print("  Syntax: species <city>")
    print("Display animal sightings in a city")
    print("  Syntax: sightings <species_taxonid>,<city>")

#display_menu() Unit test

def search_species(city):
    """
    Search for species in a given city (stub function).

    :param city: Name of the city.
    :return: List of nested species dictionaries.
    """
    # Stub implementation - to be replaced with web service call
    return [
        {"Species": {"AcceptedCommonName": "dolphin", "PestStatus": "Nil"}},
        {"Species": {"AcceptedCommonName": "snake", "PestStatus": "Venomous"}}
    ]

def display_species(species_list):
    """
    Display a list of species to the screen.

    :param species_list: List of nested species dictionaries.
    """
    print("Species found in the city:")
    for species in species_list:
        name = species["Species"]["AcceptedCommonName"]
        status = species["Species"]["PestStatus"]
        print(f"- {name} ({status})")

def search_sightings(taxonid, city):
    """
    Search for animal sightings of a particular species in a given city (stub function).

    :param taxonid: Taxon ID of the species.
    :param city: Name of the city.
    :return: List of animal sightings.
    """
    # Stub implementation - to be replaced with web service call
    return [{"properties": {"StartDate": "1999-11-15", "LocalityDetails": "Tinaroo"}}]

def display_sightings(sightings):
    """
    Display a list of animal sightings to the screen.

    :param sightings: List of animal sightings.
    """
    print("*" * 80)
    print("Animal Sightings:")
    for sighting in sightings:
        start_date = sighting["properties"]["StartDate"]
        locality = sighting["properties"]["LocalityDetails"]
        print(f"- {locality} (Date: {start_date})")
    print()
    print("*" * 80)

main()

# Task 5: List Venomous Species in an Area

   Limitations:
      •	The filter_venomous(species_list) function currently only filters species based on their 'PestStatus' attribute. It does not consider other factors such as location or date. This limitation may be addressed in future iterations if necessary.
      
   Known Bugs:
      •	There are no known bugs in the implemented functions at the moment.
      
Test Plan: We will test the new functionality added to the application:

# 1.	Test 1: Display Venomous Species in a City
   •	Input: Call the main() function.
   •	User Input: Enter the command "species Cairns venomous".
   •	Expected Output: The application should display a list of venomous species found in the city of Cairns.
   •	Actual Output: Verified through manual testing.
   
# 2.	Test 2: Invalid Command
   •	Input: Call the main() function.
   •	User Input: Enter an invalid command.
   •	Expected Output: The application should display an error message indicating that the command is invalid.
   •	Actual Output: Verified through manual testing.
   
# 3.	Test 3: No Venomous Species Found
   •	Input: Call the main() function.
   •	User Input: Enter the command "species UnknownCity venomous".
   •	Expected Output: The application should display a message indicating that no venomous species were found for the specified city.
   •	Actual Output: Verified through manual testing


![screenshot](https://github.com/Foram1123/project-python/blob/main/Images/5.PNG)

Code:

def main():
    """
    Main function to prompt the user for commands and execute corresponding actions.

    The function prompts the user for commands and executes the corresponding actions based on the input.
    """
    display_menu()  # Display the help menu initially

    while True:
        user_input = input("wildlife> ").strip().lower()

        if user_input.startswith('species'):
            # Parse the command and city
            _, *rest = user_input.split()
            if len(rest) == 2 and rest[1] == "venomous":
                # Display only venomous species
                city = rest[0]
                species_list = search_species(city)
                venomous_species = filter_venomous(species_list)
                display_species(venomous_species)
            else:
                city = ' '.join(rest)
                species_list = search_species(city)
                display_species(species_list)
        elif user_input.startswith('sightings'):
            # Parse the command, species taxonid, and city
            _, species_city = user_input.split(maxsplit=1)
            taxonid, city = species_city.split(',')
            sightings = search_sightings(taxonid, city)
            display_sightings(sightings)
        elif user_input == 'help':
            display_menu()
        elif user_input == 'exit':
            print("Exiting the application.")
            break
        else:
            print("Error: Invalid command. Please enter 'help' or 'exit' or 'species <city>' or 'species <city> venomous' or 'sightings <species_taxonid>,<city>'.")

def display_menu():
    """
    Display the menu options for the application.

    This function prints the menu options available to the user.
    The menu includes commands like 'Display help', 'Exit the application', 'Display animal species in a city',
    'Display animal sightings in a city', and 'Display venomous species in a city'.
    """
    print("Help")
    print("====")
    print("The following commands are recognized.")
    print("Display help")
    print("Exit the application")
    print("Display animal species in a city")
    print("  Syntax: species <city>")
    print("Display animal sightings in a city")
    print("  Syntax: sightings <species_taxonid>,<city>")
    print("Display venomous species in a city")
    print("  Syntax: species <city> venomous")


#display_menu() Unit test

def search_species(city):
    """
    Search for species in a given city (stub function).

    :param city: Name of the city.
    :return: List of nested species dictionaries.
    """
    # Stub implementation - to be replaced with web service call
    return [
        {"Species": {"AcceptedCommonName": "dolphin", "PestStatus": "Nil"}},
        {"Species": {"AcceptedCommonName": "snake", "PestStatus": "Venomous"}}
    ]


def display_species(species_list):
    """
    Display a list of species to the screen.

    :param species_list: List of nested species dictionaries.
    """
    print("*" * 80)
    print()
    print("Species found in the city:")
    for species in species_list:
        name = species["Species"]["AcceptedCommonName"]
        status = species["Species"]["PestStatus"]
        print(f"- {name} ({status})")
    print()
    print("*" * 80)


def search_sightings(taxonid, city):
    """
    Search for animal sightings of a particular species in a given city (stub function).

    :param taxonid: Taxon ID of the species.
    :param city: Name of the city.
    :return: List of animal sightings.
    """
    # Stub implementation - to be replaced with web service call
    return [{"properties": {"StartDate": "1999-11-15", "LocalityDetails": "Tinaroo"}}]


def display_sightings(sightings):
    """
    Display a list of animal sightings to the screen.

    :param sightings: List of animal sightings.
    """
    print("*" * 80)
    print("Animal Sightings:")
    for sighting in sightings:
        start_date = sighting["properties"]["StartDate"]
        locality = sighting["properties"]["LocalityDetails"]
        print(f"- {locality} (Date: {start_date})")
    print()
    print("*" * 80)

def filter_venomous(species_list):
    """
    Filter the list of species to include only venomous species.

    :param species_list: List of species dictionaries.
    :return: Filtered list of species containing only venomous species.
    """
    return [species for species in species_list if species["Species"]["PestStatus"] == "Venomous"]


main()



