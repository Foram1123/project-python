## Week 09

# Task 6: Add a GPS Stub

Limitations:
        •	The gps(city) function currently acts as a stub and always returns Brisbane's GPS coordinates. This limitation will be addressed in future iterations of the application when integration with a web service is implemented.
    
Known Bugs:
        •	There are no known bugs in the implemented functions at the moment.
    
Test Plan: We will test the functionality added to the application:

  1.	Test 1: Check GPS Coordinates for Brisbane
     
                •	Input: Call the gps(city) function with "Brisbane".
                •	Expected Output: The function should return Brisbane's GPS coordinates: {"latitude": -27.4689682, "longitude": 153.0234991}.
                •	Actual Output: Verified using assert statements.

![screenshot](https://github.com/Foram1123/project-python/blob/main/Images/Part%202/6.PNG)

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
    # Get GPS coordinates for the city
    coordinates = gps(city)

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

def gps(city):
    """
    Return GPS coordinates for a given city.

    :param city: Name of the city.
    :return: Dictionary containing latitude and longitude.
    """
    # Stub implementation - always return Brisbane's GPS coordinates
    return {"latitude": -27.4689682, "longitude": 153.0234991}

# Assert statements to check GPS coordinates for Brisbane
assert gps("Brisbane") == {"latitude": -27.4689682, "longitude": 153.0234991}

main()


