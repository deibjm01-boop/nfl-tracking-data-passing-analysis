# NFL Tracking Data Passing Analysis

Analysis of how **receiver separation, quarterback pressure, and passing lane occupation** influence passing efficiency in the NFL using **tracking data and Apache Spark**.

This project uses player tracking data to study spatial factors that impact offensive efficiency, measured through **Expected Points Added (EPA)**.

---

# Project Overview

Passing performance in the NFL is strongly influenced by spatial dynamics on the field.  
Using tracking data from the **NFL Big Data Bowl**, this project investigates how three key factors affect offensive efficiency:

- Receiver separation from defenders
- Quarterback pressure and pocket cleanliness
- Defensive occupation of the passing lane

The objective is to understand how these elements influence **Expected Points Added (EPA)** and passing outcomes.

---

# Data Sources

The analysis combines multiple datasets:

- **NFL Big Data Bowl (Kaggle)**  
  Tracking data containing player positions, velocities, and play context.

- **nflverse repository**  
  Additional play-level and contextual information.

Due to size restrictions, raw datasets are **not included in this repository**.

---

# Project Pipeline
NFL Tracking Data
↓
Data Processing with PySpark
↓
Feature Engineering
↓
Query-Based Analysis
↓
EPA-Based Insights
↓
Visualizations and Interpretation

---

# Research Questions

The project explores four analytical questions.

---

## 1️⃣ Receiver Separation by Coverage

How much separation does each coverage scheme allow, and how does it translate into offensive value?

Key metrics:

- Average receiver separation
- Open rate (>3.5 yards)
- Average EPA

![Coverage Separation](visuals/query1_coverage_separation_vs_epa.png)

Key insight:

- **Cover 2 Zone** allows both high separation and high EPA.
- **Man coverage** generates fewer windows but can be heavily punished when broken.

---

## 2️⃣ Linebacker Reaction to Play Action

This analysis measures how linebackers react to play action and how that reaction affects offensive efficiency.

Metrics analyzed:

- Linebacker displacement toward the line of scrimmage
- Acceleration toward the line
- EPA on play action passes

![LB Bite](visuals/query2_linebacker_bite_vs_play_action_epa.png)

Key insight:

Stronger linebacker reactions often correlate with higher offensive EPA, but only when quarterbacks exploit the space created.

---

## 3️⃣ Pocket Cleanliness and Blitz

This analysis studies the relationship between:

- Pocket pressure
- Blitz frequency
- Time to throw
- Offensive efficiency

![Blitz Pocket](visuals/query3_pocket_blitz_epa_heatmap.png)

Key insight:

Blitzes reduce time to throw but can increase EPA because they weaken pass coverage.

---

## 4️⃣ Passing Lane Occupation

This section quantifies how many defenders occupy the passing lane between the quarterback and the targeted receiver.

![Passing Lane](visuals/query4_passing_lane_defenders_epa_heatmap.png)

Key insight:

Completion probability drops significantly as more defenders occupy the passing lane.

---

# Repository Structure
nfl-tracking-data-passing-analysis
│
├── README.md
├── LICENSE
│
├── notebook
│   └ nfl_tracking_analysis.ipynb
│
├── visuals
│   └ query1_coverage_separation_vs_epa.png
│   └ query1_kmeans_elbow_method.png
│   └ query1_team_offensive_profiles_clusters.png
│   └ query2_linebacker_bite_vs_play_action_epa.png
│   └ query2_play_action_epa_by_lb_bite_level.png
│   └ query3_pocket_blitz_epa_heatmap.png
│   └ query4_passing_lane_defenders_epa_heatmap.png
│   └ query4_pass_outcome_by_passing_lane_defenders.png
│
├── presentation
│   └ presentation_analysis.pdf
│
└── data
    └ README.md
