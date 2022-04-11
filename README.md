# Analyzing Amazon reviews
## Overview of the analysis

   Analyze Amazon reviews to allows manufacturers and publishers to receive reviews for their products by performing the following
   Perform ETL on Amazon Product Reviews
   Determine Bias of Vine Reviews
   
   
## Result 
STEP 2: create a new DataFrame or table to retrieve all the rows where the number of helpful_votes divided by total_votes is equal to or greater than 50%.
helpful_votes = total_votes20.filter("(helpful_votes/total_votes) >= 0.5")
helpful_votes.show(5)
 --------------+-----------+-------------+-----------+----+-----------------+
|     review_id|star_rating|helpful_votes|total_votes|vine|verified_purchase|
+--------------+-----------+-------------+-----------+----+-----------------+
|R2WOW0TURNXB26|          3|           54|         59|   N|                Y|
|R13VL62Y2HBQ0B|          5|           15|         21|   N|                Y|
|R22G55KAPZKJQV|          4|           20|         21|   N|                Y|
|R1610PGTJS7G3N|          2|           28|         44|   N|                Y|
| RLQL04BL0QXOJ|          4|           45|         47|   N|                Y|
+--------------+-----------+-------------+-----------+----+-----------------+
only showing top 5 rows


STEP 3 :Filter the DataFrame or table created in Step 2, and create a new DataFrame or table that retrieves all the rows where a review was written as part of the Vine program (paid), vine == 'Y'.
vineY = helpful_votes.filter(helpful_votes["vine"] == 'Y')
vineY.show(5)

    review_id|star_rating|helpful_votes|total_votes|vine|verified_purchase|
+--------------+-----------+-------------+-----------+----+-----------------+
|R1MAOLI5FJHAFM|          4|          249|        261|   Y|                N|
| R9PYAUDIBJVEC|          4|           12|         22|   Y|                N|
| R6V9SHMMG5M8F|          5|          101|        110|   Y|                N|
|R37PVLT6ELL5J4|          4|          181|        209|   Y|                N|
| R2FSFGWZF24V9|          4|           50|         51|   Y|                N|
+--------------+-----------+-------------+-----------+----+-----------------+
only showing top 5 rows


STEP 4 : Repeat Step 3, but this time retrieve all the rows where the review was not part of the Vine program (unpaid), vine == 'N'.
vineN = helpful_votes.filter(helpful_votes["vine"] == 'N')
vineN.show(5)

-------------+-----------+-------------+-----------+----+-----------------+
|     review_id|star_rating|helpful_votes|total_votes|vine|verified_purchase|
+--------------+-----------+-------------+-----------+----+-----------------+
|R2WOW0TURNXB26|          3|           54|         59|   N|                Y|
|R13VL62Y2HBQ0B|          5|           15|         21|   N|                Y|
|R22G55KAPZKJQV|          4|           20|         21|   N|                Y|
|R1610PGTJS7G3N|          2|           28|         44|   N|                Y|
| RLQL04BL0QXOJ|          4|           45|         47|   N|                Y|
+--------------+-----------+-------------+-----------+----+-----------------+
only showing top 5 rows
 
 
## Summary 
There are 9002021 total reviews / 
There are 4824725 5-star reviews / 
There are 0.0 % 5-star vine (vine = Y) reviews
