# 🎬 Netflix Data Analysis & Visualization Project

Welcome to the **Netflix Data Analysis & Visualization** project. This project demonstrates an end-to-end data pipeline: importing raw data into **MySQL** for data cleaning, transformation, and query analysis, then connecting to **Power BI** to build an interactive, high-fidelity business intelligence dashboard.

---

## 🎯 Project Goals & Objectives

The primary goals of this project are:
1. **Data Modeling & Storage:** Load the raw Netflix dataset into a structured relational database using **MySQL**.
2. **Data Cleaning & Preprocessing:** Use SQL queries to handle missing values, resolve formatting discrepancies, clean text fields, and organize the data.
3. **Exploratory Data Analysis (EDA):** Write advanced SQL queries to analyze content distribution, identify top-producing countries, track yearly additions, and discover genre popularity.
4. **Interactive Dashboard Design:** Establish a connection between MySQL and **Power BI** to build a modern, interactive dashboard with KPI metrics, historical trends, geographical mapping, and dynamic slicers.

---

## 📂 Project Files

This workspace contains the following key files:
*   **`netflix_titles.csv`**: The raw dataset containing metadata for Netflix movies and TV shows (including titles, directors, cast, country, release year, rating, duration, genres, and descriptions).
*   **`netflix.pbix` / `netflix2.pbix` / `netflix (1).pbix`**: Power BI Desktop files containing the visual analytics dashboard, calculations, and data relationships.
*   **`mysql_concept.png`**: A high-quality custom graphic illustrating the MySQL database layer.
*   **`powerbi_concept.png`**: A high-quality custom graphic illustrating the Power BI analytics layer.

---

## 💾 MySQL Database Layer

**MySQL** serves as the central data store and query engine for this project.


### 1. Database Schema Definition
```sql
CREATE DATABASE netflix_db;
USE netflix_db;

CREATE TABLE netflix_titles (
    show_id VARCHAR(10) PRIMARY KEY,
    type VARCHAR(20),
    title VARCHAR(255),
    director VARCHAR(255),
    cast TEXT,
    country VARCHAR(255),
    date_added VARCHAR(50),
    release_year INT,
    rating VARCHAR(10),
    duration VARCHAR(50),
    listed_in TEXT,
    description TEXT
);
```

### 2. Key Analytical SQL Queries
*   **Content Type Distribution (Movies vs. TV Shows):**
    ```sql
    SELECT type, COUNT(*) as total_count
    FROM netflix_titles
    GROUP BY type;
    ```
*   **Top 5 Content-Producing Countries:**
    ```sql
    SELECT country, COUNT(*) as total_content
    FROM netflix_titles
    WHERE country IS NOT NULL AND country != ''
    GROUP BY country
    ORDER BY total_content DESC
    LIMIT 5;
    ```

---

## 📊 Power BI Analytics & Dashboard

**Power BI** is utilized to build a clean, dynamic dashboard with real-time slicing and query capabilities.



### 1. Key Dashboard Features:
*   **Key Performance Indicators (KPIs):** Instant metrics for Total Titles, Total Movies, and Total TV Shows.
*   **Content Split:** A donut chart visual representing the ratio of Movies to TV Shows in the catalog.
*   **Release & Additions Trends:** Line charts mapping the volume of new releases over time.
*   **Geographic Visualizations:** An interactive map highlighting global content production hot-spots.
*   **Classification & Genre Breakdown:** Bar charts showing the most prominent content ratings (e.g., TV-MA, PG-13) and popular genres (e.g., Documentaries, Dramas).
*   **Interactive Slicers:** Dynamic filters allowing users to slice data by Year, Content Type, Country, or Genre.

---

## 🛠️ Getting Started & Setup

1. Create the database schema in your **MySQL Server** and import the data from `netflix_titles.csv`.
2. Open the `.pbix` project file using **Power BI Desktop**.
3. Update the **Data Source Settings** to point to your local or cloud MySQL instance.
4. Interact with the visual elements and filter the dashboard!
