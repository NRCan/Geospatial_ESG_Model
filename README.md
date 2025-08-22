# Geospatial_ESG_Model
A CMGD initiative which provides ESG (Environmental, Social, and Governance) ratings and conflict probabilities for geographic locations.

## What is this API?

The Geospatial ESG Model combines public datasets (e.g., conservation, governance, biodiversity, land use) to predict:

- ESG ratings (percentile-based, 0–100 scale)  
- Conflict probability (0–1 scale)

Higher ESG ratings indicate lower risk. Higher conflict probabilities indicate greater potential for disputes or disruptions.


## Available Endpoints

1. **`/single`** – Query a single location.
2. **`/multiple`** – Query multiple locations at once.

All endpoints use **POST** to handle larger input payloads and maintain consistency.


## Input Format

### Single Location Request (JSON):

```json
{
  "latitude": 45.425,
  "longitude": -75.695
}
```
### Multiple Locations Request (JSON):

```json
[
  { "latitude": 45.425, "longitude": -75.695 },
  { "latitude": 43.651, "longitude": -79.347 }
]
```

## Output Format

### Example API Response:
```json
{
  "S2_ID": "4cce04f",
  "RATING_ENVIRONMENTAL": 2,
  "RATING_SOCIAL": 24,
  "RATING_GOVERNANCE": 87,
  "RATING_ESG": 52,
  "PROBABILITY": 0.986118498629639
}
```

### Response Descriptions:

  - `S2_ID`: Unique alphanumeric identifier based on resolution 12 of the S2 discrete global grid system;

  - `RATING_ENVIRONMENTAL`: environmental rating (0–100), higher environmental ratings are interpreted as being associated with lower spatially situated risks;

  - `RATING_SOCIAL`: social rating (0–100), higher social ratings are interpreted as being associated with lower spatially situated risks.

  - `RATING_GOVERNANCE`: governance rating (0–100), higher governance ratings are interpreted as being associated with lower spatially situated risks.

  - `RATING_ESG`: total environmental, social, governance (ESG) rating (0–100), higher ESG ratings are interpreted as being associated with lower spatially situated risks.

  - `PROBABILITY`: Likelihood (0–1) of disputes, protests and other forms of natural resources conflict based on the preferred deep learning model. Higher probabilities are interpreted as being associated with higher spatially situated risks.
