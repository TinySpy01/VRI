import pandas as pd  # pip install pandas openpyxl
import plotly.express as px  # pip install plotly-express
import streamlit as st  # pip install streamlit


# emojis: https://www.webfx.com/tools/emoji-cheat-sheet/
st.set_page_config(page_title="VRI27", page_icon=":seedling:",layout='wide')


df = pd.read_excel(
            io="test_lbd1.xlsx",
            engine="openpyxl",
            sheet_name="Feuil1",
            skiprows=0,
            usecols="A:C",
            nrows=49,
        )
df2 = pd.read_excel(
            io="MétéoCasa.xlsx",
            engine="openpyxl",
            sheet_name="Table 0",
            skiprows=0,
            usecols="A:F",
            nrows=16,
        )   



image1,vide,vide1,vide2,image2=st.columns(5)

with image1:
    st.image("logolbd.png",width=120)
with vide:
    st.write('')
with vide1:
    st.title("SMART VRI")
with vide2:
    st.write('')
with image2:
    st.image("ecole-centrale-casablanca.png",width=120)
st.markdown("##")

avg_temp=round(df["Temperature"].mean(),1)
avg_hum=round(df["Humidité"].mean(),1)
temp_meteo=df2._get_value(1,"Conditions Temperature")
hum_meteo=df2._get_value(1,"Comfort Humidity")
precip_meteo=df2._get_value(1,'Precipitation Amount')

Temp_column,Hum_column,Forecastecolumn=st.columns(3)

with Temp_column:
    st.write('Température moyenne du champ:')
    st.write(avg_temp,"°C")
with Hum_column:
    st.write('Humidité moyenne du champ:')
    st.write(avg_hum)
with Forecastecolumn:
    st.write('Météo:')
    st.write(f"Temp.(max/min): {temp_meteo}🌤")
    st.write(f'Humidité: {hum_meteo}a')
    st.write(f'Précipitations:{precip_meteo}')


st.markdown('----')

hist_hum=px.bar(df,
                    x="TIME",
                    y="Humidité",
                    template="plotly_white",

                    )                
hist_hum.update_layout(bargap=0.2,
                        plot_bgcolor="rgba(0,0,0,0)",
                        xaxis=(dict(showgrid=False))
)

temp,vide3,meteo=st.columns(3)
with temp:
    st.write('Variation de la Température')
    st.plotly_chart(hist_hum)

with meteo:
    button=st.button("Météo (Casablanca)")
    if button:
        on_click=st.table(df2)
with vide3:
    st.write("")



hide_st_style = """
                <style>
                #MainMenu {visibility: hidden;}
                footer {visibility: hidden;}
                header {visibility: hidden;}
                </style>
                """
st.markdown(hide_st_style, unsafe_allow_html=True)
