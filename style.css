import streamlit as st
import pandas as pd
import plost
from PIL import Image

# Page setting
st.set_page_config(layout="wide") 

# Load custom CSS
with open('Streamlit_dashboard/style.css') as f:
    st.markdown(f'<style>{f.read()}</style>', unsafe_allow_html=True) 

# Load Data
seattle_weather = pd.read_csv('https://raw.githubusercontent.com/tvst/plost/master/data/seattle-weather.csv', parse_dates=['date'])

# Get the most recent data row
latest_data = seattle_weather.iloc[-1] 

latest_wind = latest_data['wind']
latest_temp = latest_data['temp_max']
latest_weather = latest_data['weather'] 

# Row A - logo + dynamic wind
a1, a2, a3 = st.columns(3)
a1.image(Image.open('Streamlit_dashboard\canva-cloudy-wather-icon-MAE_XEFcv8o.png'))
a2.metric("Wind", f"{latest_wind:.1f} mph")
a3.metric("Weather", latest_weather.capitalize()) 

# Row B - temperature, wind, weather repeated or add more
b1, b2, b3, b4 = st.columns(4)
b1.metric("Max Temperature", f"{latest_temp:.1f} °F")
b2.metric("Wind", f"{latest_wind:.1f} mph")
b3.metric("Weather", latest_weather.capitalize())
b4.metric("Date", latest_data['date'].strftime('%Y-%m-%d')) 

# Row C - Main chart (Temperature Heatmap only)
st.markdown('### Seattle Temperature Heatmap')
plost.time_hist(
    data=seattle_weather,
    date='date',
    x_unit='week',
    y_unit='day',
    color='temp_max',
    aggregate='median',
    legend=None
)
