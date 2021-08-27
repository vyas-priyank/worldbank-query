# World Bank

* meta data - No.of Rows x Columns
* Summary Stats
*  Univariate(Single Column)
*  Histogram, Density Plot - Frequency
*  Bivariate (Two Columns)
*  Scatter Plot - Correlation

# of Countries

```sql
SELECT  count(distinct country_code) FROM `patents-public-data.worldbank_wdi.wdi_2016`
```
Ans:264

# Min year and Max Year
```sql
SELECT min(year) as min_year, max(year) as max_year FROM  `patents-public-data.worldbank_wdi.wdi_2016`
```
Ans:1960 min_year
    2016 max_year
    
# to find the indicator surface
```sql
SELECT * 
FROM `patents-public-data.worldbank_wdi.wdi_2016`
where  lower(indicator_name) like '%surface%'
limit 1000
```

# Avg  Min and max surface areas of all the countries in the dataset

```sql
SELECT  min(indicator_value) as min_surface_area, max(indicator_value) as max_surface_area, avg(indicator_value) as average_surface_area
FROM  `patents-public-data.worldbank_wdi.wdi_2016`
```
# For each country we require

```sql
SELECT country_name,  
min(indicator_value) as min_surface_area, 
max(indicator_value) as max_surface_area, 
avg(indicator_value) as average_surface_area
FROM  `patents-public-data.worldbank_wdi.wdi_2016`
group by country_name
```
Ans:
![image](https://user-images.githubusercontent.com/89662666/131186338-759c55e7-f537-48ea-9f62-b2f82f1fb4bd.png)

# Arranging them in descending

```sql
SELECT country_name, 
min(indicator_value) as min_surface_area, 
max(indicator_value) as max_surface_area, 
avg(indicator_value) as average_surface_area
FROM  `patents-public-data.worldbank_wdi.wdi_2016`
where 1=1
and indicator_name = 'Surface area (sq. km)'
group by country_name
order by average_surface_area desc 
```

#Avg CO2 emissions by countries


