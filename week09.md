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
