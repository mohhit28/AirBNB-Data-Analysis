# AirBNB-Data-Analysis
Report Analysis: Airbnb Data Analysis Project
# 1. Overview
•	Document Title: Air Bnb Data Analysis Project
•	Date and Time: March 22, 2025, 3:13 PM
•	Format: HTML export from a Jupyter Notebook
•	Purpose: The project analyzes Airbnb listing data to explore distributions of prices, room types, neighborhoods, and review trends over time.
•	Dataset: "Airbnb_Open_Data.csv" (assumed to contain 102,599 rows and 26 columns initially, reduced to 101,410 rows and 24 columns after cleaning).
•	Tools Used: Python libraries including pandas, matplotlib.pyplot, and seaborn.
# 2. Data Loading and Initial Exploration
•	Loading the Data: 
o	The dataset is loaded using pandas with the command df = pd.read_csv("Airbnb_Open_Data.csv").
o	A DtypeWarning indicates that column 25 has mixed data types, suggesting potential data quality issues. The warning recommends specifying dtype or setting low_memory=False, though no action is explicitly taken in the code provided.
•	Initial View: 
o	The dataset includes columns such as id, NAME, host id, host_identity_verified, host name, neighbourhood group, and others.
o	Sample entries show listings like "Clean & quiet apt home by the park" and "Skylit Midtown Castle," with host verification status and neighborhood details.
# 3. Data Cleaning
•	Column Identification: 
o	The dataset has 26 columns, including id, price, room type, neighbourhood group, last review, license, and house_rules.
•	Missing Values: 
o	Missing value counts are calculated using df.isnull().sum(): 
	NAME: 250 missing
	host_identity_verified: 289 missing
	host name: 406 missing
	last review: 15,893 missing
	reviews per month: 15,879 missing
	house_rules: 52,131 missing
	license: 102,597 missing (nearly all rows)
o	Columns like id, host id, and room type have no missing values.
•	Handling Missing Values: 
o	The license and house_rules columns are dropped using df.drop(columns=["license", "house_rules"], errors='ignore') due to their high missing value rates (especially license, missing in 99.9% of rows).
o	An attempt to convert last review to datetime is shown (df['last review'] = pd.to_datetime()), but the code appears incomplete or corrupted (e.g., "pd.to thanks"), indicating a potential error in execution or OCR transcription.
o	The cleaned dataset has 101,410 rows and 24 columns.
# 4. Descriptive Statistics
•	Key Metrics: 
o	Descriptive statistics are generated using df.describe() for numerical columns: 
	id: Mean ~29.2M, Min 1.001254M, Max 57.36742M
	host id: Mean ~49.26B, Min 123.6M, Max 98.76B
	lat: Mean 40.728, Min 40.49979, Max 40.91697 (consistent with New York City coordinates)
	long: Mean -73.949, Min -74.24984, Max -73.70522
	Construction year: Mean 2012.49, Min 2003, Max 2022
	price: Mean $625.36, Min $50, Max $1200 (incomplete data in OCR for full range)
# •	Observations: 
o	The latitude and longitude ranges align with New York City, suggesting the dataset is NYC-specific.
o	The Construction year spans 2003–2022, indicating a mix of older and newer properties.
# 5. Visualizations and Insights
The project includes several visualizations using seaborn and matplotlib to explore the data:
1.	Distribution of Prices: 
o	Code: sns.histplot(df['price'], bins=50, kde=True, color='red')
o	Insight: The histogram shows an even distribution of prices with no significant concentration in any range. The KDE (Kernel Density Estimate) confirms a wide variety of prices.
o	Evaluation: The lack of price concentration is unusual for Airbnb data, which typically shows clustering at lower price points. This could indicate data issues or a unique dataset.
2.	Room Type Distribution: 
o	Code: sns.countplot(x='room type', data=df, color='hotpink')
o	Insight: Most listings are "Entire home/apt" and "Private room," with "Shared room" and "Hotel room" being less common.
o	Evaluation: This aligns with typical Airbnb trends, where entire homes and private rooms dominate due to guest preferences for privacy.
3.	Neighborhood Analysis: 
o	Code: sns.countplot(y='neighbourhood group', data=df, color="lightgreen", order=df['neighbourhood group'].value_counts().index)
o	Insight: Manhattan and Brooklyn have the most listings, followed by Queens, the Bronx, and Staten Island.
o	Evaluation: This reflects NYC’s real-world Airbnb market, where Manhattan and Brooklyn are popular tourist and residential areas.
4.	Price vs. Room Type: 
o	Code: sns.boxplot(x='room type', y='price', hue='room type', data=df, palette='Set1')
o	Insight: 
o	The box plot reveals that "Shared room" listings generally have lower prices, consistent with their communal nature, while "Private room," "Entire home/apt," and "Hotel room" exhibit higher and more varied price ranges. "Entire home/apt" and "Hotel room" likely show the widest spread due to factors like size, amenities, and location premiums, though outliers may also reflect luxury listings or data entry errors.
o	Evaluation: This visualization effectively highlights pricing dynamics, offering practical insights for hosts setting competitive rates or guests seeking budget options. The UserWarning about the legend suggests a minor coding oversight (redundant hue parameter), but it doesn’t detract from the plot’s clarity.
o	Reviews Over Time: 
o	Code: An attempt to plot reviews over time begins with df['last review'] = pd.to_datetime(), but the code is incomplete or corrupted (e.g., "pd.to thanks" and trailing nonsensical characters). The intended visualization is a line plot of review counts over time.
o	Insight: The accompanying text suggests the plot would show trends in review activity, with potential spikes or drops indicating periods of high or low engagement. These could correlate with external factors like holidays, policy changes, or market shifts.
o	Evaluation: While the concept is promising for understanding listing popularity and user behavior, the lack of a completed plot limits its immediate value. Properly executed, this could be a standout feature of the analysis, revealing temporal patterns critical for strategic planning.
o	Additional Observations:
o	Data Quality: The dataset’s integrity is partially compromised by missing values (e.g., 15,893 in last review) and mixed data types (column 25 warning). These issues are acknowledged but not fully resolved beyond dropping columns, which may affect the robustness of insights.
o	Scope: The analysis focuses on descriptive statistics and visualizations without advancing to predictive modeling or statistical testing, keeping it exploratory rather than inferential.
o	________________________________________
# o	Conclusion
o	The "Airbnb Data Analysis Project" dated March 22, 2025, offers a solid exploratory analysis of Airbnb listings, likely in New York City, based on geographic coordinates. It effectively uses pandas, matplotlib, and seaborn to clean the dataset—reducing it from 102,599 rows and 26 columns to 101,410 rows and 24 columns—and visualize key trends. Notable findings include an even price distribution (unusual for Airbnb data), a prevalence of "Entire home/apt" and "Private room" listings, and a concentration of listings in Manhattan and Brooklyn. Pricing varies significantly by room type, with "Shared room" being the cheapest and "Entire home/apt" showing the broadest range.
o	While the visualizations provide actionable insights for hosts, guests, or market analysts, the analysis is hampered by incomplete code (e.g., last review conversion and reviews-over-time plot) and unaddressed data quality issues like missing values and mixed types. These gaps suggest either execution errors or OCR transcription flaws. The project excels as a descriptive overview but falls short of its potential for deeper temporal or predictive insights due to these limitations.
o	To enhance its impact, future iterations should resolve coding issues, fully handle missing data (e.g., imputation or subset analysis), and complete the temporal review analysis to uncover engagement trends. With these improvements, the project could evolve into a more comprehensive tool for understanding Airbnb market dynamics as of early 2025, offering strategic value beyond its current exploratory scope.
o	

