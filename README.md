# 🚕 Uber Hot Zones in New York — Unsupervised Clustering

> Finding the areas of New York where Uber pickups concentrate, by day and hour, so drivers can be positioned **before** demand peaks.
> *Jedha Data Science certification project — RNCP35288, Block 3 (unsupervised machine learning).*

---

## 🎯 Business problem
Uber wants to cut waiting times by recommending **hot zones** to drivers: moving from a reactive to a proactive logic, with cars already in the right place at the right time.

## 📊 Data
- Uber pickups in New York, **April to August 2014**: **3.5 million trips** (3,481,313 after keeping only New York coordinates)
- Each trip: date/time, latitude, longitude → engineered `hour` and `day_of_week`
- 2015 data excluded (zone IDs only, no GPS coordinates)

## 🔍 Key EDA insights
- Demand peaks **between 5 pm and 7 pm** (end of the working day)
- **Monday–Thursday** are busier than weekends; weekend demand spreads to residential and leisure areas
- Activity grows over the summer months

## 🛠️ Approach
| Step | Method |
|---|---|
| Number of zones | Elbow method + **silhouette score** |
| **K-Means** | k = 8 → **silhouette ≈ 0.44** · model cached to avoid recomputation |
| **DBSCAN** | `eps` estimated from the k-distance graph (0.004), `min_samples = 15` |
| Visualisation | Interactive **Plotly** maps per weekday and hour |

## ✅ Results
- **K-Means (k = 8)** produces compact, interpretable zones: Manhattan (Midtown, Financial District), Brooklyn, Queens and the airports. Cluster centres can be sent directly to drivers as target locations.
- **DBSCAN** with these parameters merged all points into **a single cluster**: pickups in New York are so dense that zones connect. It needs smaller `eps`, larger `min_samples`, or running per time slot to reveal sub-zones.
- ➡️ **Recommendation: K-Means** for a real-time driver app (one parameter, stable, cluster centres usable as coordinates).

## 💡 Business recommendations
1. **Dynamic driver allocation**: send drivers to hot clusters ~30 minutes before peaks (e.g. 5 pm on weekdays)
2. **Targeted driver communication** in the app, by day and hour
3. Watch growing outer clusters (Brooklyn, Queens) for new driver bases

## 🧰 Tech stack
`Python` · `pandas` · `scikit-learn` (K-Means, DBSCAN, silhouette) · `Plotly` · `joblib`

## 📁 Repository
```
├── Uber_ds3.ipynb    # full analysis
├── models/           # cached K-Means / DBSCAN models
├── uber-trip-data/   # monthly trip files
└── requirements.txt
```

---
👤 **Nouman Malidi Mlimi** — Data Scientist / Data Analyst · [Portfolio](https://noumanmalidi7.github.io) · [LinkedIn](https://www.linkedin.com/in/nouman-malidi-a99276326/)
