# **Netflix-data_analysis_using_PowerBI**

## **Overview**
This project analyzes Netflix data using Power BI to extract insights about content trends, genres, and audience preferences. The analysis includes creating measures, relationships, and visualizations to present key findings.

---

## **Dataset Details**
The dataset consists of two tables:

### **1. Titles**
- **Columns**:
  - `id`: Unique identifier for each title  
  - `title`: Name of the movie/TV show  
  - `type`: Movie or Show  
  - `release_year`: Year of release  
  - `age_certification`: Age rating  
  - `runtime`: Runtime in minutes  
  - `genres`: Content genres  
  - `production_countries`: Countries involved in production  
  - `seasons`: Number of seasons (if applicable)  
  - `imdb_id`, `imdb_score`, `imdb_votes`: IMDb-related data  
  - `tmdb_popularity`, `tmdb_score`: TMDb-related data  

### **2. Credits**
- **Columns**:
  - `person_id`: Unique identifier for each person  
  - `id`: Related title ID  
  - `name`: Name of the person (e.g., directors, actors)  
  - `character`: Character name  
  - `role`: Role in the production (e.g., director, actor)  

---

## **Power BI Workflow**

### **1. Establishing Relationships**
- Created a relationship between the **Titles** and **Credits** tables using the `id` column.
- **Cardinality**: Many-to-One.

### **2. Measures Created**
- **Runtime in Hours**:  
  ```DAX
  Runtime(hrs) = SUM(titles[runtime]) / 60
  ```
  - Total runtime: **7,513.35 hours**.

- **Total Content**:  
  ```DAX
  Total Content = COUNTA(titles[title])
  ```
  - Total number of titles: **5,806**.

- **Movies Count**:  
  ```DAX
  Movies = CALCULATE([Total Content], titles[type] = "Movie")
  ```
  - Total movies: **3,759**.

- **Shows Count**:  
  ```DAX
  Shows = CALCULATE([Total Content], titles[type] = "Show")
  ```
  - Total shows: **2,047**.

- **Average IMDb Score**:  
  ```DAX
  Avg_imdb = AVERAGEA(titles[imdb_score])
  ```
  - Average IMDb score: **5.94**.

### **3. Visualizations**
1. **Top 5 Genres by Content**:
   - Created a stacked bar chart showing the top 5 genres based on total content.

2. **Content by Year**:
   - Created a line chart displaying yearly trends for movies and shows, filtered for releases after 2000.

3. **Subscribers by Country**:
   - Created a map highlighting viewer concentration by country, with bubble sizes representing runtime.

4. **Movies vs. Shows Ratio**:
   - Created a donut chart showing the percentage distribution of movies vs. shows.

5. **Interactive Slicers**:
   - Added dropdown slicers for:
     - Release year  
     - Title  
     - Genre  

### **4. Customization**
- Applied theme customization for better visual appeal.
- Adjusted the layout for improved readability.

---

## **Key Insights**
- **Genre Popularity**: The top 5 genres dominate Netflix’s content library.  
- **Yearly Trends**: Content production has grown significantly since 2000.  
- **Regional Insights**: The USA and India are key Netflix markets.  
- **Content Distribution**: Movies account for ~65% of total content, while shows account for ~35%.  
- **Runtime Analysis**: Netflix’s total runtime is over 7,500 hours.

---

## **Power BI Dashboard**
![Alt text](https://github.com/Abdulwaashim/Netflix-data_analysis_using_PowerBI/blob/main/Dashboard-img.png)

---

## **Future Improvements**
- Incorporate user engagement metrics for deeper analysis.
- Perform predictive analytics to forecast future content trends using advanced DAX.

---

## **How to Use This Repository**
1. Clone the repository:
   ```bash
   git clone https://github.com/Abdulwaashim/Netflix-data_analysis_using_PowerBI.git
   ```
2. Open the Power BI file (`Netflix analysis01.pbix`) in Power BI Desktop.
3. Explore the visuals and interact with the slicers for customized insights.
