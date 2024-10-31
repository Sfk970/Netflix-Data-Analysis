# Netflix-Data-Analysis
### Problem Statement
With the proliferation of streaming services, understanding viewer preferences and content performance is crucial for platforms like Netflix. This project aims to analyze Netflix's catalog data to uncover trends, identify popular genres and titles, understand viewer ratings and preferences, and examine content distribution and release patterns. The ultimate goal is to provide strategic recommendations for content acquisition, marketing efforts, and enhancing viewer engagement.

## Data Preparation
### Data Source
Netflix Dataset: This dataset includes movies, TV shows, ratings, and release dates.

### Data Cleaning and Transformation
Remove Duplicate Entries: Ensured each sale is unique.

Handle Missing Values: Filled in missing values or removed incomplete entries.

Standardize Formats: Standardized date formats and corrected any inconsistencies.

Data Loading: Imported the cleaned data into PowerBI for visualization.

## Queries Used
### Popular Genres:
SELECT genre, COUNT(*) as count
FROM netflix1
GROUP BY genre
ORDER BY count DESC
LIMIT 10;

### Monthly Additions:
SELECT country, release_year as year, EXTRACT(MONTH FROM date_added) AS month, COUNT(*) AS total_content
FROM netflix1
WHERE country IS NOT NULL AND date_added IS NOT NULL
GROUP BY country, year, month
ORDER BY total_content desc;

### Content Release Trends:
SELECT release_year, COUNT(*) AS count FROM netflix1
GROUP BY release_year
ORDER BY release_year desc;

### Content Distribution in top countries:
SELECT country, release_year as year, EXTRACT(MONTH FROM date_added) AS month, COUNT(*) AS total_content
FROM netflix1
WHERE country IS NOT NULL AND date_added IS NOT NULL
GROUP BY country, year, month
ORDER BY total_content desc;

### Directors with most content across multiple countries:
SELECT director, COUNT(DISTINCT country) AS country_count, COUNT(*) AS total_content
FROM netflix1
WHERE director IS NOT NULL AND country IS NOT NULL
GROUP BY director
HAVING country_count > 1
ORDER BY total_content DESC;

### Popular Genres:
SELECT release_year, listed_in AS genre, COUNT(*) AS total_content
FROM netflix1
GROUP BY release_year, genre
ORDER BY release_year, genre;

## Visualizations Used
### Area Chart

Description: Total movies and TV shows by release year.

Insights: Displays trends in content release over the years.

### Slicer

Description: Allows filtering by movies or TV shows.

Insights: Enables detailed analysis by content type.

### Map Visualization:

Description: Geographical distribution of content.

Insights: Shows where movies and TV shows have been released globally.

### Stacked Column Chart

Description: Total movies and TV shows by country.

Insights: Highlights the distribution of movies and TV shows across different countries.

### Stacked Bar Chart

Description: Total movies and TV shows by directors.

Insights: Provides insights into the output of different directors.

### Cards for Key Metrics

Description: Total TV shows and movies, total ratings, and genre information.

Insights: Quick overview of content volume and rating quality.


## Key Insights
Popular Genres: Drama and Comedy are the leading genres.

Monthly Additions: Notable spikes in content additions during certain months.

Average Rating by Genre: Documentaries tend to receive higher ratings.

Content Distribution: The USA produces the most content on Netflix.

Top Rated Content: The highest-rated titles include a mix of critically acclaimed movies and TV shows.

