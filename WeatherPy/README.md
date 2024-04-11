# python-api-challenge
Module 6
This challenge has been split into two sub-challenges. The first 'WeatherPy' tasked me with obtaining the weather from the 'OpenWeatherMap API' for 500 cities across the world, with the data collected being output to a CSV file before being read into the second task 'VacationPy'. In the second task, using the data within the CSV, locate hotels using the 'Geoapify API' within certain Cities to plan my next vacation!

WeatherPy :Obtaining the Data
- Citipy libary code already provided to obtain a random selection of Longitude and Latitude values and the nearest City.
- Using the 'OpenWeatherMap API' iterate through the cities identified by the Citipy:
    - Through the JSON result for each city obtain:
        - Latitude
        - Longitude
        - Max Temp
        - Humidity
        - Cloud cover
        - Wind speed
        - Country code
        - Date
    - Append the obtained data to the 'city_data' list
- Create a dataframe from the 'city_data' list
    - Save the dataframe to CSV ready for the 'VacationPy' task
Generate Scatter plots
- Using the data collected, generate scatter plots for:
    - Latitude vs Temperature (c)
    - Latitude vs. Humidity (%)
    - Latitude vs. Cloudiness (%)
    - Latitude vs. Wind Speed (m/s)
- Note: To save time/repetitve coding, I created a function to generate the base scatter plots and then just added additional lines for the titles/labels
Compute Linear Regression
- Separate the Citie's from the previous dataframe into Northern and Southern Hemisphere dataframes
- Create a function to compute the linear regression for the previously created plots, broken down into Northern and Southern Hemisphere dataframes
- Create plots, linear regression and Line Equation for the following relationships:
    - Northern Hemisphere: Temperature vs. Latitude
    - Southern Hemisphere: Temperature vs. Latitude
    - Northern Hemisphere: Humidity vs. Latitude
    - Southern Hemisphere: Humidity vs. Latitude
    - Northern Hemisphere: Cloudiness vs. Latitude
    - Southern Hemisphere: Cloudiness vs. Latitude
    - Northern Hemisphere: Wind Speed vs. Latitude
    - Southern Hemisphere: Wind Speed vs. Latitude

VacationPy: Plot the Cities on a World Map  
Using the CSV from the previous 'city_data_df' plot each City on a hvplot world map
- The size of the marker should be determined by the 'Humidity' value of each City
- And each City point should be coloured differently

Add conditions to limit the number of Cities
Added three conditions to reducde the number of cities down:
    - Temperature should be <= 30
    - Temperature should be >= 20
    - Cloudiness should be == 0
The reduced dataset is then renamed to 'hotel_df' consisting of the following columns:
    - City
    - Country
    - Longitude
    - Latitude
    - Humidity
    - Hotel Name - This was an empty column added to the dataframe ready for the next task

Locate nearest Hotel to each City in 'hotel_df'
Using the 'Geoapify API' iterate through each City within the 'hotel_df' and find:
 - The nearest Hotel
 - Within 10km of the Latitude and Longitude of the city
 - Append the name of the hotel to the 'Hotel Name' column of the DataFrame
- I added an additional step to filter out any Cities where a hotel was not found within the search area
- Using the 'hotel_df' generate another world map to show each City which met the previous conditions set
 - Add the 'Hotel Name' and 'Country' to the hover message for each point
