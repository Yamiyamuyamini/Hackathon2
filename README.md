# Hackathon2
Install pandas using (pip install pandas)
Import both pandas and matplotlib ,here pandas is used to analysis the data and matplotlib is used to visualize the data (import pandas as pd and import matplotlib.pyplot as mp
Read the data from the csv file format (=pd.read_csv) give path to the data and it will read the data 
For every data i have searched whether there are any null values (isnull().sum()) 
-->For the first question:
# Analyze the adoption rate of electric vehicles over the years. How has the demand for EVs changed over time?
EC['Date']=pd.to_datetime(EC['Date'])
EC['Year']=EC['Date'].dt.year  ## extracting year from date
EC = EC[['Date', 'Year'] + EC.columns.drop(['Date', 'Year']).tolist()]  ##moving year to the 2nd column
EC1=EC.groupby('Year',as_index=False).sum(numeric_only=True)  ##grouping them and adding
EC1.head()
Analysis:
# based adoption rate of elctrical vechiles over the years ,I want to mention first four years like which is the most used based on my analysis
# 1-> year:2001  Two Wheeler (NT) vehicles are mostly used
# 2-->year:2002  LIGHT GOODS VEHICLE are mostly used
# 3-->year:2003  LIGHT GOODS VEHICLE are mostly used
# 4-->year:2004  LIGHT MOTOR VEHICLE are mostly used
--->For the second one
## Compare the performance of different EV manufacturers. Which companies have the highest market share, and what factors contribute to their success?
S_m['Total_Sales'] = S_m.iloc[:, 2:].sum(axis=1)# Sum sales across all years for each manufacturer
total_sales = S_m['Total_Sales'].sum()
S_m['Market_Share'] = (S_m['Total_Sales'] / total_sales) * 100 # Calculate market share for each manufacturer
S_m['Total_Sales'] = S_m['Total_Sales'].round(0)
S_m['Market_Share'] = S_m['Market_Share'].round(0)
sorted_data = S_m[['Maker', 'Total_Sales', 'Market_Share']].sort_values(by='Market_Share', ascending=False) # Sort manufacturers by market share
sorted_data.head()# Display top manufacturers by market share
Analysis:
# considering the share distribution of market  OLA Electric Technologies PVT LTD has the highest share rating of 38.2% compared with other markets
# because its offering affordable, high-performance products to customers.
---> For the third question
## Investigate the relationship between the price of EVs and their features. Is there a correlation between price and key attributes such as battery life, range, or charging time?
Answer:
# This question is not related to the data but when we consider it,there is a relation between the price and their features like battery life, range, and charging time.
# Electrical vechicles with higher prices tend to have better performance in these areas

-->For the fourth question
##  Explore the impact of government subsidies or regulations on the EV market. Have policy changes resulted in noticeable shifts in sales or adoption rates?
Answer:
# This is also not related to the data,but government subsidies and regulations have a significant positive impact on the EV market, often leading to noticeable shifts in sales and adoption rates, with purchase subsidies being particularly effective in stimulating short-term EV sales
# while policies promoting charging infrastructure development contribute to long-term adoption

---> For the fifth question
## Study how the demand for electric vehicles varies across different regions in India. Which regions are leading in EV adoption, and what might be the reasons behind this trend?
state = E_v['State'].value_counts().reset_index()
state.columns = ['State', 'EV_Maker']
state_sorted =state.sort_values(by='EV_Maker', ascending=False)
state_sorted.head()
Analysis:
# Based on the above consideration i conclude that maharashtra is the highest when compared to other regions because may be they sell the best product with low cost

--->For the sixth question
## Analyze the potential environmental benefits of increasing EV adoption. What is the reduction in emissions or fuel consumption?
Answer:
# This question is also not related to the data they provided
# Increasing EV adoption can significantly reduce greenhouse gas emissions by replacing internal combustion engine vehicles, which emit CO₂ and other pollutants. It also lowers fuel consumption, cutting reliance on fossil fuels and improving air quality.
# The overall impact depends on the energy mix used for charging—greater benefits arise from renewable-powered grids.
