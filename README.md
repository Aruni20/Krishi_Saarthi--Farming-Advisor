
# Krishi Saarthi: AI-Powered Farming Advisor
**From Soil to Strategy — One Platform for Smart Farming**

## Overview
Can AI help Indian farmers make better, data-driven agricultural decisions — without needing to understand the technology behind it?

Krishi Saarthi transforms soil quality, weather forecasts, and local farming practices into personalized, voice-based crop recommendations in local languages. By combining machine learning, large language models (LLMs), and clustering techniques, it builds an intelligent advisory system that is interpretable, inclusive, and deployable.

From predicting suitable crops to summarizing yield-maximizing practices and reading out agriculture news in local languages, Krishi Saarthi aims to democratize precision agriculture for every farmer.

## Motivation
Despite India's rich agro-climatic diversity, most farmers rely on heuristics rather than data. Access to scientific advice is often:

- **Delayed** (outdated reports, offline channels)
- **Inaccessible** (language/literacy barriers)
- **Generic** (not personalized by region or soil)

Krishi Saarthi bridges this gap by offering a localized, personalized, and interpretable farming assistant—powered by AI, but designed for practical use.

## Research Objectives
- Can we recommend crops based on soil and weather inputs using supervised machine learning?
- Can unsupervised clustering identify region-specific best practices?
- Can we convert statistical outputs into non-technical summaries using LLMs?
- Can the system generate voice-based output in vernacular languages?
- Can farmers receive local agriculture news summaries via crop/state filters?

## System Architecture

```
[Farmer Input]

    │
    ▼
Soil Health Data Scraper
(N, P, K, pH from SHC)

    │
    ▼
Weather Forecast Module
(Rainfall, Temp, Humidity)
→ [Feature Vector]

    │
    ▼
Crop Recommender (ML Model)
(Random Forest Classifier)
→ Suitable Crop

    │
    ▼
Farming Style Clustering
(KMeans on actual crop data)
→ Style 1 | Style 2 | ...

    │
    ▼
Cluster Yield Analysis
(Compare yield/input ratio)
→ Best ROI Practice

    │
    ▼
GPT / Mistral Summarizer
(LLM-based explanation)
→ Readable Summary

    │
    ▼
News Scraper + Summarizer
(Krishi Jagran via crop/state)
→ Local Agri News

    │
    ▼
Voice Output (gTTS)
(Local language conversion)
→ Audio in Hindi/Bengali/etc
```

## Data Sources & APIs

| Source           | Role                                    |
|------------------|-----------------------------------------|
| SHC Portal       | NPK and pH soil health values           |
| OpenWeatherMap   | 7-day weather forecast                  |
| Local CSVs       | Historical crop/yield/fertilizer data   |
| Krishi Jagran    | Agricultural news scraping              |
| gTTS             | Voice synthesis in Indian languages     |

## ML Pipeline Highlights

### 1. Crop Recommendation (Supervised Learning)
- **Input**: [N, P, K, pH, Rainfall, Temp, Humidity]
- **Model**: After testing various models, Random Forest consistently provided the highest accuracy and was selected for deployment.
- **Output**: Most suitable crop (e.g., Maize, Wheat)

### 2. Farming Style Discovery (Unsupervised Learning)
- **Applied only to predicted crop**
- **Clustered on**: Fertilizer, Pesticide, Season, Area, Rainfall
- **Output**: 3–4 styles (e.g., Rainfed low-input, Balanced Kharif)

### 3. LLM Summary Generator
Converts cluster statistics into natural language summaries:

Example: Balanced Kharif maize gives 2.7 t/ha yield using 120kg fertilizer and 2kg pesticide. Ideal for small farmers.

## Localized Advisory Features
- Scrapes Krishi Jagran using [Crop + State] as filters
- Uses LLM to generate 1–2 line summary:

Example: New maize procurement scheme in Bihar — ₹2,000/ha subsidy till July 25.

- Added to voice output along with crop and practice insights

## Deployment & Accessibility
- Built on Streamlit for rapid UI prototyping
- Final output is:
  - Displayed as text on the interface
  - Played as audio in the regional language
- **Hosting**: Streamlit Cloud / HuggingFace Spaces

## Modular Codebase

| Module               | Folder                          | Description                                |
|----------------------|----------------------------------|--------------------------------------------|
| Weather Fetcher      | 1_weather_forecasting/           | Pulls OpenWeatherMap forecast              |
| Soil Scraper         | 2a_soil_data_scraper/            | Fetches NPK and pH from SHC                |
| Crop Classifier      | 2_crop_recommendation/           | ML model prediction                        |
| Cluster Analysis     | 3_farming_styles_clustering/ and 4_cluster_analysis/ | Clusters and evaluates styles |
| LLM Summary Generator| 5_llm_summary/                   | GPT/Mistral-based simplification           |
| Agri News Summarizer | 6_news_scraper/                  | Scrapes and summarizes agriculture news    |
| Voice Output         | 7_gtts_voice_output/             | Converts summary to local language audio   |
| UI & Integration     | app/                             | Streamlit frontend with full pipeline      |

## Deployment & Accessibility

The system is deployed via **Streamlit**, enabling rapid prototyping and interactive web-based delivery.

### Final Output Format:
- **Text**: Recommendations are displayed in structured natural language.
- **Audio**: Automatically played in the user's selected regional language via text-to-speech synthesis.

### Hosting:
Available at: [krishisaarthi.streamlit.app](https://krishisaarthi.streamlit.app)


## Impact

- **Localized Decision Support**: District-specific recommendations tailored to soil and weather
- **Inclusive AI**: Audio outputs in regional languages enhance accessibility for low-literacy users
- **Data-to-Practice Bridge**: Converts technical metrics into practical farming strategies

## Example Output (Voice and Text)
"In your district, maize is best grown during Kharif using 120kg fertilizer and 2kg pesticide. This gives 2.7 tonnes/ha yield.  
Also, a new maize subsidy of ₹2,000/ha is available till July 25.  
Recommended style is Balanced Kharif: moderate input with high ROI."

(Played in Hindi or Telugu via gTTS)

## Why It Matters

| Stakeholder     | Value Delivered                                       |
|------------------|------------------------------------------------------|
| Farmers          | Timely, local, and easy-to-understand guidance       |
| Agri Scientists  | Real-world deployment of ML models in agriculture    |
| Government/NGOs  | Low-cost, scalable precision advisory platform       |
| Researchers      | Applied ML + LLM pipeline on tabular and textual data|

## How to Run
```bash
git clone https://github.com/your_username/krishi-saarthi.git
cd krishi-saarthi
pip install -r requirements.txt
streamlit run app/app.py
```

## Keywords
Smart Farming, Crop Recommendation, Precision Agriculture, LLM, gTTS, Soil Data, Weather Forecast, Cluster Farming, Multilingual AI, AgriTech India, XGBoost, KMeans, Streamlit, Explainable AI

---

Krishi Saarthi integrates domain expertise, machine learning methodologies, and natural language processing into a unified advisory system — providing scalable and interpretable agricultural intelligence at the grassroots level.
