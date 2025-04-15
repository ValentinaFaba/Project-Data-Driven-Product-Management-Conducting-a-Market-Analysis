# Project-Data-Driven-Product-Management-Conducting-a-Market-Analysis
This project helps the fitness studio explore interest in workouts at a global and national level.
I explore local and international markets to find opportunities for the fitness products. I used data manipulation skills to examine data about online interest in home gyms, gym workouts, home workouts, and fitness products, and create visualizations to help guide the product decisions.

Instructions:

-When was the global search for 'workout' at its peak? 

-Of the keywords available, what was the most popular during the covid pandemic, and what is the most popular now?

-What country has the highest interest for workouts among the following: United States, Australia, or Japan? 

-You'd be interested in expanding your virtual home workouts offering to either the Philippines or Malaysia. Which of the two countries has the highest interest in home workouts?


### The Data
CSV files in the "Files/data" folder, which offer international and national-level data on Google Trends keyword searches related to fitness and related products. 

### workout.csv

| Column     | Description              |
|------------|--------------------------|
| `'month'` | Month when the data was measured. |
| `'workout_worldwide'` | Index representing the popularity of the keyword 'workout', on a scale of 0 to 100. |

### three_keywords.csv

| Column     | Description              |
|------------|--------------------------|
| `'month'` | Month when the data was measured. |
| `'home_workout_worldwide'` | Index representing the popularity of the keyword 'home workout', on a scale of 0 to 100. |
| `'gym_workout_worldwide'` | Index representing the popularity of the keyword 'gym workout', on a scale of 0 to 100. |
| `'home_gym_worldwide'` | Index representing the popularity of the keyword 'home gym', on a scale of 0 to 100. |

### workout_geo.csv

| Column     | Description              |
|------------|--------------------------|
| `'country'` | Country where the data was measured. |
| `'workout_2018_2023'` | Index representing the popularity of the keyword 'workout' during the 5 year period. |

### three_keywords_geo.csv

| Column     | Description              |
|------------|--------------------------|
| `'country'` | Country where the data was measured. |
| `'home_workout_2018_2023'` | Index representing the popularity of the keyword 'home workout' during the 5 year period. |
| `'gym_workout_2018_2023'` | Index representing the popularity of the keyword 'gym workout' during the 5 year period.  |
| `'home_gym_2018_2023'` | Index representing the popularity of the keyword 'home gym' during the 5 year period. |

# Import the necessary libraries and csv files
import pandas as pd
import matplotlib.pyplot as plt
workout = pd.read_csv('data/workout.csv')
keywords = pd.read_csv('data/three_keywords.csv')
workout_geo = pd.read_csv('data/workout_geo.csv')
keywords_geo = pd.read_csv('data/three_keywords_geo.csv')
#Find the time of peak searches for workout
peak = workout['workout_worldwide'].max()
peak_month = workout.loc[workout['workout_worldwide'] == peak,'month'].iloc[0]
year_str = peak_month.split('-')[0]
print('The year when the global search for workout was in its peaks was', year_str)
#Use visualization to identify the highest value for 'workout' searches.
plt.figure(figsize=(12,6))
plt.plot(workout['month'], workout['workout_worldwide'])
plt.xticks(rotation = 90)
plt.xlabel('Date')
plt.ylabel('Index 0-100')
plt.title('Global search of the word "workout"')
plt.show()
