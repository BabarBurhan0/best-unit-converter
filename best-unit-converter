import streamlit as st
from datetime import datetime

# --- Page Config ---
st.set_page_config(
    page_title="Unit Converter",
    page_icon="🔄",
    layout="centered",
)

# --- Styling ---
st.markdown(
    """
    <style>
        .main {
            background-color: #f4f4f4;
        }
        .block-container {
            padding-top: 2rem;
            padding-bottom: 2rem;
        }
        .stButton>button {
            background-color: #4CAF50;
            color: white;
            font-weight: bold;
        }
        .stRadio>div {
            gap: 1rem;
        }
    </style>
    """,
    unsafe_allow_html=True
)

# --- Conversion Functions ---
def length_converter(value, choice):
    if choice == "Kilometers to Miles":
        return f"🌍 {value} km = {value * 0.621371:.2f} miles"
    elif choice == "Miles to Kilometers":
        return f"🛣️ {value} miles = {value * 1.60934:.2f} km"

def weight_converter(value, choice):
    if choice == "Kilograms to Pounds":
        return f"🏋️ {value} kg = {value * 2.20462:.2f} pounds"
    elif choice == "Pounds to Kilograms":
        return f"⚖️ {value} pounds = {value * 0.453592:.2f} kg"

def temperature_converter(value, choice):
    if choice == "Celsius to Fahrenheit":
        return f"🌡️ {value}°C = {(value * 9/5) + 32:.2f}°F"
    elif choice == "Fahrenheit to Celsius":
        return f"🌡️ {value}°F = {(value - 32) * 5/9:.2f}°C"

# --- App Layout ---
def main():
    st.title("🔄 Universal Unit Converter")
    st.markdown("Convert **Length**, **Weight**, or **Temperature** with ease.")

    if "history" not in st.session_state:
        st.session_state.history = []

    with st.sidebar:
        st.header("🕓 Conversion History")
        if st.session_state.history:
            for item in reversed(st.session_state.history):
                st.write(item)
        else:
            st.write("No conversions yet.")

    option = st.selectbox(
        "📦 Choose Category",
        ["Length Converter", "Weight Converter", "Temperature Converter"]
    )

    if option == "Length Converter":
        st.header("📏 Length Converter")
        choice = st.radio("Conversion Type", ["Kilometers to Miles", "Miles to Kilometers"])
        value = st.number_input("Enter value", min_value=0.0, format="%.2f")
        if st.button("Convert"):
            result = length_converter(value, choice)
            st.success(result)
            st.session_state.history.append(f"[{datetime.now().strftime('%H:%M:%S')}] {result}")

    elif option == "Weight Converter":
        st.header("🏋️ Weight Converter")
        choice = st.radio("Conversion Type", ["Kilograms to Pounds", "Pounds to Kilograms"])
        value = st.number_input("Enter value", min_value=0.0, format="%.2f")
        if st.button("Convert"):
            result = weight_converter(value, choice)
            st.success(result)
            st.session_state.history.append(f"[{datetime.now().strftime('%H:%M:%S')}] {result}")

    elif option == "Temperature Converter":
        st.header("🌡️ Temperature Converter")
        choice = st.radio("Conversion Type", ["Celsius to Fahrenheit", "Fahrenheit to Celsius"])
        value = st.number_input("Enter value", format="%.2f")
        if st.button("Convert"):
            result = temperature_converter(value, choice)
            st.success(result)
            st.session_state.history.append(f"[{datetime.now().strftime('%H:%M:%S')}] {result}")

if __name__ == "__main__":
    main()
