# Hotel-Revenue-Data-Analysis
Analyzed Hotel Revenue Trends with SQL

# SQL Code
#Union all 3 tables 
WITH revenue_data AS (
    SELECT * FROM hotel.hotel_2018
    UNION ALL
    SELECT * FROM hotel.hotel_2019
    UNION ALL
    SELECT * FROM hotel.hotel_2020
)
SELECT * FROM revenue_data;


#calculating revenue and saved it new column Total_revenue, rounding up to an integer
WITH revenue_data AS (
    SELECT * FROM hotel.hotel_2018
    UNION ALL
    SELECT * FROM hotel.hotel_2019
    UNION ALL
    SELECT * FROM hotel.hotel_2020
)
select arrival_date_year, hotel,
ROUND(sum((stays_in_week_nights+stays_in_weekend_nights)*adr)) as Total_revenue from revenue_data
group by arrival_date_year, hotel;


#The first left join connects revenue_data with the hotel.market_segment table based on the common column market_segment.
#The second left join connects revenue_data with the hotel.mealcost_hotel table based on the common column meal
The second left join connects revenue_data with the hotel.mealcost_hotel table based on the common column meal
WITH revenue_data AS (
    SELECT * FROM hotel.hotel_2018
    UNION ALL
    SELECT * FROM hotel.hotel_2019
    UNION ALL
    SELECT * FROM hotel.hotel_2020
)

select * from revenue_data left join hotel.market_segment on revenue_data.market_segment=market_segment.market_segment 
left join hotel.mealcost_hotel on mealcost_hotel.meal=revenue_data.meal;
