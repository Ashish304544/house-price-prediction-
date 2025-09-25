
import streamlit as st
import pandas as pd
import pickle


#Loading the saved model
loaded_model = pickle.load(open('C:/Users\AYUSHMAN PANDEY\Desktop\ML PROJECT DEPLOYMENT\model_and_mapping.pkl', 'rb'))

model = loaded_model["model"]
location_mapping = loaded_model["location_mapping"]


st.set_page_config(page_title="House Price Prediction", layout="centered")
st.title("🏠Welcome to California House Price Predictor")

# Location dropdown
selected_location = st.selectbox("Select Location", list(location_mapping.keys()))

# Auto-fill based on selected location
population = location_mapping[selected_location]["Population"]
latitude = location_mapping[selected_location]["Latitude"]
longitude = location_mapping[selected_location]["Longitude"]

st.write(f"**Population:** {population}")
st.write(f"**Latitude:** {latitude}")
st.write(f"**Longitude:** {longitude}")

# Other inputs
median_income = st.number_input("Median Income(10K $)", min_value=0.0, format="%.2f")
house_age = st.number_input("House Age", min_value=0, format="%d")
avg_rooms = st.number_input("Average Rooms", min_value=0.0, format="%.2f")
avg_bedrooms = st.number_input("Average Bedrooms", min_value=0.0, format="%.2f")

# Prediction
if st.button("Predict Price"):
    
    input_df = pd.DataFrame([{
        "MedInc": median_income,
        "HouseAge": house_age,
        "AveRooms": avg_rooms,
        "AveBedrms": avg_bedrooms,
        "Population": population,
        "Latitude": latitude,
        "Longitude": longitude,
        "Location": selected_location
    }])

    input_df = input_df.drop(columns=["Location"])

# droping location bcoz xgboost takes numerical input , but Location is a string 

    prediction = model.predict(input_df)[0]
    
    price_usd = prediction * 100000
    price_inr = price_usd * 85  

    st.success(f"Estimated Price: ${price_usd:,.2f} USD")
    st.success(f"Estimated Price: ₹{price_inr:,.2f} INR") 

   
    
