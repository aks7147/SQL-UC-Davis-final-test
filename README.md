# SQL-UC-Davis-final-test
SQL for Data Science- UC Davis University Week 4 FInal test

Part 1: Yelp Dataset Profiling and Understanding

1. Profile the data by finding the total number of records for each of the tables below:
	
i. Attribute table = 10000 records
ii. Business table = 10000 records
iii. Category table = 10000 records
iv. Checkin table = 10000 records
v. elite_years table = 10000 records
vi. friend table = 10000 records
vii. hours table = 10000 records
viii. photo table = 10000 records 
ix. review table = 10000 records
x. tip table = 10000 records
xi. user table = 10000 records
	


2. Find the total distinct records by either the foreign key or primary key for each table. If two foreign keys are listed in the table, please specify which foreign key.

i. Business = 10000 records
ii. Hours = 1562 records
iii. Category = 2643 records
iv. Attribute = 1115 records
v. Review = 8090 records
vi. Checkin = 493 records
vii. Photo = 10000 records
viii. Tip = 537 record
ix. User = 10000 records
x. Friend = 11 records
xi. Elite_years = 2780 records

Note: Primary Keys are denoted in the ER-Diagram with a yellow key icon.	



3. Are there any columns with null values in the Users table? Indicate "yes," or "no."

	Answer:No
	
	
	SQL code used to arrive at answer:select id
, name, review_count, yelping_since, useful, funny, cool, fans, average_stars
, compliment_hot, compliment_more, compliment_profile, compliment_cute, compliment_list, compliment_note, compliment_plain, compliment_cool, compliment_funny, compliment_writer, compliment_photos

from user
where id = NULL or name = NULL or review_count = NULL or yelping_since = NULL or useful = NULL or funny = NULL or cool = NULL or fans= NULL or average_stars= NULL or compliment_hot= NULL or compliment_more= NULL or compliment_profile= NULL or compliment_cute= NULL or compliment_list= NULL or compliment_note= NULL or compliment_plain = NULL or compliment_cool= NULL or compliment_funny= NULL or compliment_writer= NULL or compliment_photos= NULL;

	
	

	
4. For each table and column listed below, display the smallest (minimum), largest (maximum), and average (mean) value for the following fields:

	i. Table: Review, Column: Stars
	
		min:	1	max:	5	avg: 	3.7082
		
	
	ii. Table: Business, Column: Stars
	
		min:	1	max:	5	avg:	3.6549
		
	
	iii. Table: Tip, Column: Likes
	
		min:	0	max:	2	avg:	0.0144
		
	
	iv. Table: Checkin, Column: Count
	
		min:	1	max:	53	avg:	1.9414
		
	
	v. Table: User, Column: Review_count
	
		min:	0	max:	2000	avg:	24.2995
		


5. List the cities with the most reviews in descending order:

	SQL code used to arrive at answer:
select
city
, count(review_count) as total_review
from business
group by city
order by total_review desc;
	
	
	Copy and Paste the Result Below:
+-----------------+--------------+
| city            | total_review |
+-----------------+--------------+
| Las Vegas       |         1561 |
| Phoenix         |         1001 |
| Toronto         |          985 |
| Scottsdale      |          497 |
| Charlotte       |          468 |
| Pittsburgh      |          353 |
| Montr??al        |          337 |
| Mesa            |          304 |
| Henderson       |          274 |
| Tempe           |          261 |
| Edinburgh       |          239 |
| Chandler        |          232 |
| Cleveland       |          189 |
| Gilbert         |          188 |
| Glendale        |          188 |
| Madison         |          176 |
| Mississauga     |          150 |
| Stuttgart       |          141 |
| Peoria          |          105 |
| Markham         |           80 |
| Champaign       |           71 |
| North Las Vegas |           70 |
| North York      |           64 |
| Surprise        |           60 |
| Richmond Hill   |           54 |
+-----------------+--------------+
(Output limit exceeded, 25 of 362 total rows shown)
	

	
6. Find the distribution of star ratings to the business in the following cities:

i. Avon

SQL code used to arrive at answer:

select
stars
, review_count
from business
where city = 'Avon';


Copy and Paste the Resulting Table Below (2 columns ??? star rating and count):
+-------+--------------+
| stars | review_count |
+-------+--------------+
|   2.5 |            3 |
|   4.0 |            4 |
|   5.0 |            3 |
|   3.5 |            7 |
|   1.5 |           10 |
|   3.5 |           31 |
|   4.5 |           31 |
|   3.5 |           50 |
|   2.5 |            3 |
|   4.0 |           17 |
+-------+--------------+


ii. Beachwood

SQL code used to arrive at answer:

select
name
, stars
, review_count
from business
where city = 'Beachwood';


Copy and Paste the Resulting Table Below (2 columns ??? star rating and count):
		
---------------------------------+-------+--------------+
| name                            | stars | review_count |
+---------------------------------+-------+--------------+
| Maltz Museum of Jewish Heritage |   3.0 |            8 |
| Charley's Grilled Subs          |   3.0 |            3 |
| Sixth & Pine                    |   4.5 |           14 |
| Beechmont Country Club          |   5.0 |            6 |
| Hyde Park Prime Steakhouse      |   4.0 |           69 |
| Origins                         |   4.5 |            3 |
| Fyodor Bridal Atelier           |   5.0 |            4 |
| College Planning Network        |   2.0 |            8 |
| Lucky Brand Jeans               |   3.5 |            3 |
| American Eagle Outfitters       |   3.5 |            3 |
| Shaker Women's Wellness         |   5.0 |            6 |
| Avis Rent A Car                 |   2.5 |            3 |
| Cleveland Acupuncture           |   5.0 |            3 |
| Studio Mz                       |   5.0 |            4 |


7. Find the top 3 users based on their total number of reviews:
		
	SQL code used to arrive at answer:

select
name
, id
, review_count
from user
order by review_count desc;	
		
	Copy and Paste the Result Below:
		
+-----------+------------------------+--------------+
| name      | id                     | review_count |
+-----------+------------------------+--------------+
| Gerald    | -G7Zkl1wIWBBmD0KRy_sCw |         2000 |
| Sara      | -3s52C4zL_DHRK0ULG6qtg |         1629 |
| Yuri      | -8lbUNlXVSoXqaRRiHiSNg |         1339 |

8. Does posing more reviews correlate with more fans?

	Please explain your findings and interpretation of the results:
Posing more reviews does not corelate with more number of fans since we can see from below table as Gerald has more number of reviews but fans are comparatively low from others.

Below is query:-	
select
name,
review_count,
fans
from user
order by review_count desc

Below is output:-
-----------+--------------+------+
| name      | review_count | fans |
+-----------+--------------+------+
| Gerald    |         2000 |  253 |
| Sara      |         1629 |   50 |
| Yuri      |         1339 |   76 |
| .Hon      |         1246 |  101 |
| William   |         1215 |  126 |
| Harald    |         1153 |  311 |
| eric      |         1116 |   16 |
| Roanna    |         1039 |  104 |
| Mimi      |          968 |  497 |
| Christine |          930 |  173 |
| Ed        |          904 |   38 |
| Nicole    |          864 |   43 |
| Fran      |          862 |  124 |
| Mark      |          861 |  115 |
| Christina |          842 |   85 |
| Dominic   |          836 |   37 |
| Lissa     |          834 |  120 |
| Lisa      |          813 |  159 |
| Alison    |          775 |   61 |
| Sui       |          754 |   78 |
| Tim       |          702 |   35 |
| L         |          696 |   10 |
| Angela    |          694 |  101 |
| Crissy    |          676 |   25 |
| Lyn       |          675 |   45 |
+-----------+--------------+------+
	
9. Are there more reviews with the word "love" or with the word "hate" in them?

	Answer:
love-1780
hate-232
	
	SQL code used to arrive at answer:
select
count (*)
from review
where text like '%love%';
	

select
count (*)
from review
where text like '%hate%';
	

10. Find the top 10 users with the most fans:

	SQL code used to arrive at answer:
select name,
id,
fans
from
user
order by fans desc limit 10	
	
	Copy and Paste the Result Below:
+-----------+------------------------+------+
| name      | id                     | fans |
+-----------+------------------------+------+
| Amy       | -9I98YbNQnLdAmcYfb324Q |  503 |
| Mimi      | -8EnCioUmDygAbsYZmTeRQ |  497 |
| Harald    | --2vR0DIsmQ6WfcSzKWigw |  311 |
| Gerald    | -G7Zkl1wIWBBmD0KRy_sCw |  253 |
| Christine | -0IiMAZI2SsQ7VmyzJjokQ |  173 |
| Lisa      | -g3XIcCb2b-BD0QBCcq2Sw |  159 |
| Cat       | -9bbDysuiWeo2VShFJJtcw |  133 |
| William   | -FZBTkAZEXoP7CYvRV2ZwQ |  126 |
| Fran      | -9da1xk7zgnnfO1uTVYGkA |  124 |
| Lissa     | -lh59ko3dxChBSZ9U7LfUw |  120 |
	
		

Part 2: Inferences and Analysis

1. Pick one city and category of your choice and group the businesses in that city or category by their overall star rating. Compare the businesses with 2-3 stars to the businesses with 4-5 stars and answer the following questions. Include your code.
	
i. Do the two groups you chose to analyze have a different distribution of hours?
		Yes

ii. Do the two groups you chose to analyze have a different number of reviews?
		Yes
         
iii. Are you able to infer anything from the location data provided between these two groups? Explain.
		Location are different. Higher ratings are for long working hours.

SQL code used for analysis:

		select
business.name
, business.city
, category.category
, business.stars
, hours.hours
, business.review_count
, business.postal_code
from (business inner join category on business.id = category.business_id) inner join hours on hours.business_id = category.business_id
where business.city = 'Mesa' 
 group by business.stars;

		
2. Group business based on the ones that are open and the ones that are closed. What differences can you find between the ones that are still open and the ones that are closed? List at least two differences and the SQL code you used to arrive at your answer.
		
i. Difference 1:
         closed business have less rating
         
ii. Difference 2:
         open business have high review count
         
         
SQL code used for analysis:

	select business.name,
business.review_count,
business.stars,
business.is_open,
category.category,
hours.hours,
business.postal_code
from (business inner join category on business.id=category.business_id)
inner join hours on hours.business_id=category.business_id
where business.city = 'Mesa'
group by business.is_open
	
3. For this last part of your analysis, you are going to choose the type of analysis you want to conduct on the Yelp dataset and are going to prepare the data for analysis.

Ideas for analysis include: Parsing out keywords and business attributes for sentiment analysis, clustering businesses to find commonalities or anomalies between them, predicting the overall star rating for a business, predicting the number of fans a user will have, and so on. These are just a few examples to get you started, so feel free to be creative and come up with your own problem you want to solve. Provide answers, in-line, to all of the following:
	
i. Indicate the type of analysis you chose to do:
         Finding correlation between the likes with the given rates and using ??like?? in the reviews. 
         
ii. Write 1-2 brief paragraphs on the type of data you will need for your analysis and why you chose that data:
         I need two sources of data (tables). First, I join these two tables based on users and business. Then I sort them based on rating to see if there is a correlation between the number of stars and likes. 
The reason I chose this analysis and thus, the data sets is that psychologists have shown that how people think about something can completely change even after a few minutes and they think that how people think just after occurrence of an event is a better representative for the quality of that event compared to what they say after thinking about it. Because tip table is related to the occurrence of the event (shopping) and they write a review after hours or even days, comparing these two tables can help us to explore the validity what psychologists claim. As the result shows there is a slight correlation between the number of likes and stars, but this correlation is not strong. So what psychologists claim seems to be fairly valid.  
		
                  
iii. Output of your finished dataset:
         +-------+-------+
| stars | likes |
+-------+-------+
|     3 |     2 |
|     5 |     2 |
|     5 |     1 |
|     5 |     1 |
|     5 |     1 |
|     5 |     1 |
|     5 |     1 |
|     5 |     1 |
|     5 |     1 |
|     5 |     1 |
|     3 |     1 |
|     4 |     1 |
|     4 |     1 |
|     4 |     1 |
|     4 |     1 |
|     4 |     1 |
|     4 |     1 |
|     4 |     1 |
|     4 |     1 |
|     4 |     1 |
|     4 |     1 |
|     4 |     1 |
|     4 |     1 |
|     4 |     1 |
|     4 |     1 |
+-------+-------+
         
iv. Provide the SQL code you used to create your final dataset:
select
  review.stars
, tip.likes
from review inner join tip on review.user_id = tip.user_id
order by tip.likes desc;
