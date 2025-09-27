# NBA-Injury_Risk_Dashboard

## 📌 Overview
This project investigates the relationship between **NBA scheduling stress** (back-to-backs, travel distance, short rest) and **player injury events**.  
The goal is to develop a **data pipeline and dashboard** that highlights high-risk stretches in the NBA schedule and validates whether they correlate with actual player injuries.  

This project mimics a real analytics team workflow:  
- **Data Engineering:** Automated ingestion and cleaning of NBA game, schedule, travel, and injury data.  
- **Data Analytics:** SQL-based transformations and risk metric calculations.  
- **Data Visualization:** Dashboards that combine schedule workload with injury timelines.  
- **Cloud Infrastructure:** Built on AWS for scalability, automation, and real-world deployment.  

---

## 🎯 Objectives
1. Build a season-level dataset of **player workload + team travel stress**.  
2. Define a **Scheduling Stress Index (SSI)** based on:
   - Back-to-backs  
   - 3-in-4s, 4-in-6s  
   - Travel miles & time zone shifts  
   - Rest days between games  
3. Overlay injuries on top of workload metrics to test correlation.  
4. Deliver insights through **PowerBI/AWS QuickSight dashboards + reports**.  
5. Demonstrate end-to-end skills in **SQL, AWS, BI tools, and collaborative workflows**.  

---

## 🏗️ Architecture
      +-------------------+
      |   NBA API / BRef  |
      +-------------------+
                |
                v
      +-------------------+
      |   AWS S3 (Raw)    |
      +-------------------+
                |
                v
      +-------------------+
      | AWS Glue / Lambda |
      +-------------------+
                |
                v
      +-------------------+
      |   AWS RDS (SQL)   |
      +-------------------+
                |
      +-------------------+
      | AWS QuickSight /  |
      | PowerBI Dashboards|
      +-------------------+

---

## 📂 Repository Structure
nba-injury-risk-dashboard/
│
├── data/
│ ├── arenas.csv # Arena coordinates (lat/long)
│ ├── injuries_sample.csv # Sample injury data
│ └── schedule_sample.csv # Sample schedule data
│
├── notebooks/
│ ├── 01_explore_data.ipynb
│ └── 02_stress_vs_injury.ipynb
│
├── src/
│ ├── nba_api_pull.py # Pull NBA game logs
│ ├── transform.py # Compute workload/stress metrics
│ ├── load_to_rds.py # Push data to AWS RDS
│ ├── stress_index.py # Calculate Scheduling Stress Index
│ └── utils.py # Helper functions
│
├── sql/
│ ├── schema.sql # Table definitions for RDS
│ └── stress_queries.sql # SQL queries for metrics & joins
│
├── dashboards/
│ ├── quicksight_screenshot.png
│ └── powerbi_dashboard.pbix
│
├── reports/
│ └── 2022_23_injury_report.pdf
│
├── requirements.txt
├── README.md
└── LICENSE

---

## 📊 Data Sources
- **NBA Player Game Logs** — via [`nba_api`](https://github.com/swar/nba_api)  
- **NBA Schedule** — [Basketball-Reference](https://www.basketball-reference.com/leagues/NBA_2024_games.html)  
- **Arena Locations** — [Kaggle: NBA Arenas Dataset](https://www.kaggle.com/datasets/schmadam97/nba-arenas-20192020)  
- **Injury Logs** — [Basketball-Reference Injury Report](https://www.basketball-reference.com/friv/injuries.fcgi)  

---

## 🛠️ Tech Stack
- **Languages:** Python (pandas, requests), SQL  
- **Data Engineering:** AWS S3, AWS Glue, AWS Lambda  
- **Database:** AWS RDS (Postgres)  
- **Analytics/Warehousing:** Redshift (optional for scaling)  
- **Visualization:** AWS QuickSight / PowerBI  
- **Collaboration:** GitHub for version control  

---

## 🚀 How to Run
1. **Clone the repo**
   ```bash
   git clone https://github.com/your-username/nba-injury-risk-dashboard.git
   cd nba-injury-risk-dashboard

2. Set up environment
   pip install -r requirements.txt

3. Run ETL pipeline
   python src/nba_api_pull.py
    python src/transform.py
    python src/load_to_rds.py


