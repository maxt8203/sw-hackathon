
# Team Grace – Accident Risk Predictor

Our entry for **Hack South West 2025** (Data 4 Good).

Around 1.2 million people die in traffic accidents every year. We wanted to see what the data says about when and where crashes cause injuries, and make it something anyone can try.

## What it does

You enter a city, the hour, the day of the week and the road conditions. The app pulls the live weather for that city and returns the chance that a crash in those conditions involves an injury, labelled Low, Medium or High.

## How it works

- **Data:** about 209,000 recorded crashes (hour, weather, road surface, lighting, traffic controls, injuries, contributing causes). [Add the dataset name and link.]
- **Model:** a random forest classifier (scikit-learn) that predicts whether a crash involves at least one injury. It's trained on hour, day of week, weather and road surface.
- **API:** a small Flask service loads the model, fetches live weather from OpenWeatherMap and returns the prediction.
- **Front end:** a Streamlit app where you enter the conditions and see the result.

## What's in the repo

- `TeamGracextracolumnpractice.ipynb` – first look at the data (column counts, distributions)
- `WEBSITE_FOR_TEAM_GRACE/model.py` – trains the model
- `WEBSITE_FOR_TEAM_GRACE/api.py` – Flask prediction API
- `WEBSITE_FOR_TEAM_GRACE/app.py` – Streamlit app

## Run it

```bash
pip install streamlit flask flask-cors scikit-learn pandas requests

# 1. put traffic_accidents.csv in WEBSITE_FOR_TEAM_GRACE/
# 2. train the model (creates model.pkl)
python model.py

# 3. start the API (needs a free OpenWeatherMap key)
export WEATHER_API_KEY=your_key
python api.py

# 4. in a second terminal, start the app
streamlit run app.py
```

## Where it stands

This is a hackathon prototype built in a weekend.

- The risk score is the probability of an injury, not of a crash happening.
- Lighting and traffic-control inputs are in the app but the model doesn't use them yet.
- The model comparison, 3D plots and forecasting from our final presentation were done in Colab and aren't in this repo.
- The judges liked the presentation. Their main feedback was that we didn't clearly connect predicting injury risk to actually reducing accidents. If we continued, that link would be the first thing to fix: for example, showing how the risk scores could guide where to place road safety measures.

## My contribution

I managed the project side for our team of 3: I set the scope and plan, split the work into tasks on a whiteboard and assigned them, ran a quick check that the app worked as expected, and designed the final presentation. The code was written mainly by two teammates, Grace Murugappan (ML & data) and Joshua Masih (website).
