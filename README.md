# WEATHER MONITORING FOR NAGPUR

### INTRODUCTION
The dataset includes weather data recorded over a specific period for Nagpur. Each entry includes the exact date and time of recording, capturing variations in meteorological parameters such as temperature, dew point, and humidity. This detailed timestamping allows for in-depth analysis of daily and seasonal weather patterns, helping to identify trends and anomalies over the observed period.

### DATASET: NAGPUR WEATHER DATASET
 
![image](https://github.com/user-attachments/assets/c3e22a6e-4903-4f3a-9d3a-ae8737cb0be9)

Number of rows: **10,497**

Number of columns: **19**

### VARIABLE DESCRIPTION
1. month: The month of the recorded data (string format).
2. time: The time of the recorded data (string format).
3. day/night: Indicates whether the data was recorded during the day or night (string format).
4. temperature: The temperature in degrees Fahrenheit (integer format).
5. condition: The weather condition (e.g., Cloudy, Haze) (string format).
6. dew_point: The dew point temperature in degrees Fahrenheit (integer format).
7. heat_index: The heat index in degrees Fahrenheit (integer format).
8. humidity_%: The humidity percentage (integer format).
9. pressure: The atmospheric pressure in inches of Mercury (Hg) (float format).
10. visibility: The visibility in miles (float format).
11. windchill: The wind chill temperature in degrees Fahrenheit (integer format).
12. Wind_direction: The direction of the wind in degrees (integer format).
13. gust: The wind gust speed in miles per hour (integer format).
14. wind_speed: The wind speed in miles per hour (integer format).
15. uv_desc: The description of the UV index (e.g., Low) (string format).
16. uv_index: The UV index (integer format).
17. clouds: The cloud cover description (e.g., OVC - Overcast, SCT - Scattered) (string format).
18. rain: A boolean indicating if it rained (True/False).
19. Rain_today: A string indicating if it rained today (Yes/No).

### GRAFANA DASHBOARD 

https://github.com/user-attachments/assets/80d07c43-77e8-49a8-87f3-e6ef200033b4

### CHARTS

1. How does humidity change over time?

**Humidity Trends Over Time**
   
<img width="614" alt="Screenshot 2024-12-06 at 10 27 22 AM" src="https://github.com/user-attachments/assets/dca8c3bf-eb41-4afb-8b6a-055f75129eda">
   
**Query:** SELECT MEAN(HumidityPercentage) FROM data GROUP BY time(1m)
   
**Observation:** Humidity levels fluctuate throughout the observed period but remain within a moderate range
   
**Insights:** The humidity trends chart for Nagpur shows significant fluctuations within the observed hour, with notable peaks around 23:00 and 23:10, indicating periods of increased moisture. The frequent variability suggests dynamic weather conditions, potentially influenced by evening cooling or local meteorological events. Overall, the chart highlights the rapid changes in humidity, which could correlate with other weather parameters for deeper analysis.

2. How does the average heat index differ across various weather conditions?

**Average Heat Index by Weather Condition**

<img width="632" alt="Screenshot 2024-12-06 at 10 41 11 AM" src="https://github.com/user-attachments/assets/f509d185-8018-484a-8c09-4dfafcbb1212">

**Query:** SELECT MEAN(HeatIndex) FROM data GROUP BY condition
   
**Observation:** Cloudy conditions have an average heat index of 71.7, haze conditions rise to 86.3, and thunder conditions peak at 90.3, indicating increasing warmth and humidity.

**Insights:** Severe weather conditions, like Thunder, are linked to higher heat indices, while cloudy weather has the lowest heat index due to less sunlight and lower humidity.

3. What is the average temperature when humidity percentage is greater than 40?

**Average Temperature Over Time**
  
<img width="627" alt="Screenshot 2024-12-06 at 11 06 06 AM" src="https://github.com/user-attachments/assets/395e7e1a-4296-464a-98f1-1ef76650b62e">

**Query:** SELECT MEAN(temperature) FROM data GROUP BY time(1m)
   
**Observation:** The average temperature shows cyclical spikes, aligning with time periods during the day.

**Insights:** This chart reveals significant temperature fluctuations within the observed period. The temperature peaks, reaching over 100°F around 22:40 and 22:50, indicate periods of intense heat. Frequent dips to around 80°F suggest intermittent cooling, possibly due to changes in weather conditions such as wind or cloud cover. This pattern of rapid temperature changes highlights the dynamic nature of the local weather, with substantial variations occurring within short time intervals.

4. How does average visibility vary across various cloud cover type?
 
**Average visibility by cloud cover type**

<img width="628" alt="Screenshot 2024-12-06 at 11 13 30 AM" src="https://github.com/user-attachments/assets/0c80632c-5b58-4a93-9607-e5df7e05f126">

**Query:** SELECT MEAN(visibility) FROM data GROUP BY clouds
   
**Observation:** Clear skies (CLR) have the highest visibility, while broken clouds (BKN) and others slightly reduce visibility.
  
**Insights:** This chart shows that few clouds offer the highest visibility at 2.80 miles, followed by clear skies at 2.78 miles. Scattered and overcast clouds provide moderate visibility at 2.56 and 2.67 miles, respectively, while broken clouds have the lowest visibility at 2.21 miles. Visibility decreases as cloud cover increases.

5.  Is there a correlation between wind speed and visibility?

**Correlation Between Wind Speed and Visibility**

<img width="624" alt="Screenshot 2024-12-06 at 11 24 53 AM" src="https://github.com/user-attachments/assets/01dce4fc-9bec-4eb8-b1aa-03d368049acc">

**Query:** SELECT MEAN(WindSpeed), MEAN(visibility) FROM data GROUP BY time(1m)
   
**Observation:** Wind speed directly affects visibility, with higher speeds generally enhancing it. Understanding this correlation can help predict visibility based on wind forecasts.

**Insights:** This chart shows that few clouds offer the highest visibility at 2.80 miles, followed by clear skies at 2.78 miles. Scattered and overcast clouds provide moderate visibility at 2.56 and 2.67 miles, respectively, while broken clouds have the lowest visibility at 2.21 miles. Visibility decreases as cloud cover increases.

6. How does the heat index differ between day and night?

**Day vs Night Comparison of Heat Index**

<img width="627" alt="Screenshot 2024-12-06 at 11 55 03 AM" src="https://github.com/user-attachments/assets/e698bcad-586b-4195-859a-050057882144">

**Query:** SELECT MEAN(HeatIndex) FROM data GROUP BY DayNight
   
**Observation:** The average heat index is higher during the day (91.0) and lower at night (82.9), indicating cooler nighttime temperatures.

**Insights:** The chart shows a clear difference in Nagpur's heat index, with daytime averaging 91.0°F and nighttime 82.9°F. This highlights significant cooling at night due to reduced solar radiation, impacting comfort levels and energy usage.
