# AirBnB MongoDB Analysis

A little assignment to practice importing and analyzing data within a MongoDB database.

<!-- Replace the contents of this file with a report, as described in the [instructions](./instructions.md). -->

## Dataset Details:

This exercise uses [AirBnb listing data of Austin, Texas, US](./data/listings.csv), downloaded from [Inside AirBnB](http://data.insideairbnb.com/united-states/tx/austin/2023-12-15/data/listings.csv.gz) as a zipped CSV file. Here is a preview of the downloaded dataset (first 20 records):

| id     | listing_url                         | scrape_id      | last_scraped | source          | name                                                        | description | neighborhood_overview                                                                                                                                                                                                                                                                                                                                                                                                   | picture_url                                                                                            | host_id | host_url                                  | host_name      | host_since | host_location | host_about                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               | host_response_time | host_response_rate | host_acceptance_rate | host_is_superhost | host_thumbnail_url                                                                                         | host_picture_url                                                                                              | host_neighbourhood | host_listings_count | host_total_listings_count | host_verifications                 | host_has_profile_pic | host_identity_verified | neighbourhood                  | neighbourhood_cleansed | neighbourhood_group_cleansed | latitude | longitude | property_type        | room_type       | accommodates | bathrooms | bathrooms_text | bedrooms | beds | amenities | price   | minimum_nights | maximum_nights | minimum_minimum_nights | maximum_minimum_nights | minimum_maximum_nights | maximum_maximum_nights | minimum_nights_avg_ntm | maximum_nights_avg_ntm | calendar_updated | has_availability | availability_30 | availability_60 | availability_90 | availability_365 | calendar_last_scraped | number_of_reviews | number_of_reviews_ltm | number_of_reviews_l30d | first_review | last_review | review_scores_rating | review_scores_accuracy | review_scores_cleanliness | review_scores_checkin | review_scores_communication | review_scores_location | review_scores_value | license | instant_bookable | calculated_host_listings_count | calculated_host_listings_count_entire_homes | calculated_host_listings_count_private_rooms | calculated_host_listings_count_shared_rooms | reviews_per_month |
|--------|-------------------------------------|----------------|--------------|-----------------|-------------------------------------------------------------|-------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------|---------|-------------------------------------------|----------------|------------|---------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------|--------------------|----------------------|-------------------|------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------|--------------------|---------------------|---------------------------|------------------------------------|----------------------|------------------------|--------------------------------|------------------------|------------------------------|----------|-----------|----------------------|-----------------|--------------|-----------|----------------|----------|------|-----------|---------|----------------|----------------|------------------------|------------------------|------------------------|------------------------|------------------------|------------------------|------------------|------------------|-----------------|-----------------|-----------------|------------------|-----------------------|-------------------|-----------------------|------------------------|--------------|-------------|----------------------|------------------------|---------------------------|-----------------------|-----------------------------|------------------------|---------------------|---------|------------------|--------------------------------|---------------------------------------------|----------------------------------------------|---------------------------------------------|-------------------|
| 5456   | https://www.airbnb.com/rooms/5456   | 20231215200307 | 2023-12-16   | city scrape     | Guesthouse in Austin · ★4.84 · 1 bedroom · 2 beds · 1 bath  |             | "My neighborhood is ideally located if you want to walk to bars and restaurants downtown, East 6th Street or Rainey Street.  The Convention Center is only 3 1/2 blocks away and a quick 10 minute walk. Whole foods store located 5 blks , easily walkable."                                                                                                                                                           | https://a0.muscache.com/pictures/14084884/b5a35a84_original.jpg                                        | 8028    | https://www.airbnb.com/users/show/8028    | Sylvia         | 2009-02-16 | "Austin, TX"  | "I am a licensed Real Estate Broker and owner of Armadillo Realty.  I attended The University of Texas at Austin and fell in love with the small town that it was back in 1979; I have been here every since.  I love the Art, Music and Film scene here in Austin.  There is so much natural beauty to enjoy as well. I especially enjoy Barton Springs Pool in the summertime along with the Zilker Hillside theater productions. SXSW, Austin City Limits Festival and the East Austin Art Studio Tour are among my favorite events. I also enjoy a sunset cruise on my canoe to Congress bridge to see the Mexican Freetail Bats come out for their nightly feeding.  "                                                                                                                                                              | within an hour     | 100%               | 97%                  | t                 | https://a0.muscache.com/im/users/8028/profile_pic/1329882962/original.jpg?aki_policy=profile_small         | https://a0.muscache.com/im/users/8028/profile_pic/1329882962/original.jpg?aki_policy=profile_x_medium         | East Downtown      | 1                   | 4                         | "['email', 'phone']"               | t                    | t                      | "Austin, Texas, United States" | 78702                  |                              | 30.26057 | -97.73441 | Entire guesthouse    | Entire home/apt | 3            |           | 1 bath         |          | 2    | []        | $101.00 | 2              | 90             | 2                      | 2                      | 90                     | 90                     | 2.0                    | 90.0                   |                  | t                | 21              | 51              | 74              | 330              | 2023-12-16            | 668               | 47                    | 1                      | 2009-03-08   | 2023-11-20  | 4.84                 | 4.88                   | 4.86                      | 4.89                  | 4.83                        | 4.73                   | 4.79                |         | f                | 1                              | 1                                           | 0                                            | 0                                           | 3.71              |
| 5769   | https://www.airbnb.com/rooms/5769   | 20231215200307 | 2023-12-16   | previous scrape | Home in Austin · ★4.91 · 1 bedroom · 1 bed · 1 shared bath  |             | Quiet neighborhood with lots of trees and good neighbors.                                                                                                                                                                                                                                                                                                                                                               | https://a0.muscache.com/pictures/23822033/ac946aff_original.jpg                                        | 8186    | https://www.airbnb.com/users/show/8186    | Elizabeth      | 2009-02-19 | "Austin, TX"  | "We're easygoing professionals that enjoy meeting new people.  I love martial arts, the outdoors, kayaking, live music, good food and positive people. I can converse in Spanish and can cook a mean Mexican dinner."                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | within an hour     | 100%               | 88%                  | t                 | https://a0.muscache.com/im/users/8186/profile_pic/1272556663/original.jpg?aki_policy=profile_small         | https://a0.muscache.com/im/users/8186/profile_pic/1272556663/original.jpg?aki_policy=profile_x_medium         | SW Williamson Co.  | 1                   | 4                         | "['email', 'phone', 'work_email']" | t                    | t                      | "Austin, Texas, United States" | 78729                  |                              | 30.45697 | -97.78422 | Private room in home | Private room    | 2            |           | 1 shared bath  |          | 1    | []        |         | 1              | 14             | 1                      | 1                      | 14                     | 14                     | 1.0                    | 14.0                   |                  |                  | 0               | 0               | 0               | 0                | 2023-12-16            | 294               | 20                    | 2                      | 2010-04-10   | 2023-12-07  | 4.91                 | 4.9                    | 4.87                      | 4.91                  | 4.94                        | 4.76                   | 4.92                |         | f                | 1                              | 0                                           | 1                                            | 0                                           | 1.76              |
| 6413   | https://www.airbnb.com/rooms/6413   | 20231215200307 | 2023-12-16   | previous scrape | Guesthouse in Austin · ★4.97 · Studio · 1 bed · 1 bath      |             | "Travis Heights is one of the oldest neighborhoods in Austin. Our house was built in 1937. We rebuilt the apartment in 2009 (well, finished and furnished it for rental then). From the studio it's a pretty easy 1-mile walk through the neighborhood to all the shops and restaurants on South Congress."                                                                                                             | https://a0.muscache.com/pictures/miso/Hosting-6413/original/029304da-074c-4fce-bf9f-48a3c90d6283.jpeg  | 13879   | https://www.airbnb.com/users/show/13879   | Todd           | 2009-04-17 | "Austin, TX"  | "We're a young family that likes to travel, we just don't get to enough. So we live vicariously through our visiting guests.  <br /> We run this little vacation rental apartment ourselves. As mentioned in the listing, it's located on our property. It's an above garage apartment that is completely separate from our home. We like to think it's a bit European to share our place with guests. We're very sensitive to guests' needs and give you plenty of space. We're happy to answer any questions about Austin, help you around town, make suggestions, and more if you'd like. We've lived in Austin for about 20 years and have been renting the studio for more than nine years and make improvements as we grow with it. Thank you for considering our place. <br /> PS. No, our profile pic was not taken in Austin:)" | N/A                | N/A                | 100%                 | f                 | https://a0.muscache.com/im/pictures/user/4f35ef11-7f37-45cf-80da-f914a6d5f451.jpg?aki_policy=profile_small | https://a0.muscache.com/im/pictures/user/4f35ef11-7f37-45cf-80da-f914a6d5f451.jpg?aki_policy=profile_x_medium | Travis Heights     | 1                   | 1                         | "['email', 'phone']"               | t                    | t                      | "Austin, Texas, United States" | 78704                  |                              | 30.24885 | -97.73587 | Entire guesthouse    | Entire home/apt | 2            |           | 1 bath         |          | 1    | []        |         | 30             | 90             | 30                     | 30                     | 90                     | 90                     | 30.0                   | 90.0                   |                  |                  | 0               | 0               | 0               | 0                | 2023-12-16            | 120               | 0                     | 0                      | 2009-12-14   | 2022-10-17  | 4.97                 | 4.99                   | 4.99                      | 4.99                  | 4.98                        | 4.87                   | 4.93                |         | f                | 1                              | 1                                           | 0                                            | 0                                           | 0.70              |
| 6448   | https://www.airbnb.com/rooms/6448   | 20231215200307 | 2023-12-16   | city scrape     | Guesthouse in Austin · ★4.97 · 1 bedroom · 2 beds · 1 bath  |             | The neighborhood is fun and funky (but quiet)! People are friendly  and you can't beat the location.                                                                                                                                                                                                                                                                                                                    | https://a0.muscache.com/pictures/4513152/4ffc1234_original.jpg                                         | 14156   | https://www.airbnb.com/users/show/14156   | Amy            | 2009-04-20 | "Austin, TX"  | "We are a family of four (with teenagers, all of us vaccinated). We love our home town and location... can't beat the park, river, and downtown. We love having guests in our garage apartment... it's fun to talk to people about their lives, hometowns, and travels. We're happy to give recommendations and want you to be comfy."                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | within an hour     | 100%               | 100%                 | t                 | https://a0.muscache.com/im/users/14156/profile_pic/1413388190/original.jpg?aki_policy=profile_small        | https://a0.muscache.com/im/users/14156/profile_pic/1413388190/original.jpg?aki_policy=profile_x_medium        | Zilker             | 1                   | 2                         | "['email', 'phone']"               | t                    | t                      | "Austin, Texas, United States" | 78704                  |                              | 30.26034 | -97.76487 | Entire guesthouse    | Entire home/apt | 2            |           | 1 bath         |          | 2    | []        | $159.00 | 3              | 365            | 3                      | 3                      | 1125                   | 1125                   | 3.0                    | 1125.0                 |                  | t                | 10              | 10              | 16              | 160              | 2023-12-16            | 312               | 21                    | 2                      | 2011-09-06   | 2023-12-04  | 4.97                 | 4.97                   | 4.96                      | 4.99                  | 4.97                        | 4.97                   | 4.89                |         | t                | 1                              | 1                                           | 0                                            | 0                                           | 2.09              |
| 8502   | https://www.airbnb.com/rooms/8502   | 20231215200307 | 2023-12-16   | city scrape     | Guest suite in Austin · ★4.56 · 1 bedroom · 1 bed · 1 bath  |             |                                                                                                                                                                                                                                                                                                                                                                                                                         | https://a0.muscache.com/pictures/miso/Hosting-8502/original/be48ea3b-6d8a-4d9b-bc13-8aa514ef246a.jpeg  | 25298   | https://www.airbnb.com/users/show/25298   | Karen          | 2009-07-11 | "Austin, TX"  | "I handle the reservations at the studio on the lower level of a house that belongs to a good friend of mine.  I really enjoy this part of town, and it is great to be offering comfortable & homey lodging for people coming from around the world to experience Austin."                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               | within a day       | 100%               | 50%                  | f                 | https://a0.muscache.com/im/users/25298/profile_pic/1330879914/original.jpg?aki_policy=profile_small        | https://a0.muscache.com/im/users/25298/profile_pic/1330879914/original.jpg?aki_policy=profile_x_medium        | East Riverside     | 1                   | 1                         | "['email', 'phone']"               | t                    | f                      |                                | 78741                  |                              | 30.23466 | -97.73682 | Entire guest suite   | Entire home/apt | 2            |           | 1 bath         |          | 1    | []        | $48.00  | 4              | 90             | 4                      | 20                     | 90                     | 90                     | 7.2                    | 90.0                   |                  | t                | 15              | 45              | 75              | 75               | 2023-12-16            | 51                | 3                     | 0                      | 2010-02-19   | 2023-05-16  | 4.56                 | 4.52                   | 4.7                       | 4.84                  | 4.87                        | 4.67                   | 4.6                 |         | f                | 1                              | 1                                           | 0                                            | 0                                           | 0.30              |
| 13035  | https://www.airbnb.com/rooms/13035  | 20231215200307 | 2023-12-17   | city scrape     | Home in Austin · ★5.0 · 2 bedrooms · 2 beds · 2 baths       |             | "East Cesar Chavez is a gentrifying urban area that remains highly diverse. Guests can walk to downtown, the Convention Center, Lady Bird Lake, Rainey Street, E. 6th Street, Franklin Barbecue, taco trailers, coffee shops, hot spots, and hidden gems."                                                                                                                                                              | https://a0.muscache.com/pictures/miso/Hosting-13035/original/00407f5f-ff1f-4653-8832-4fbeee901a83.jpeg | 50793   | https://www.airbnb.com/users/show/50793   | Molly          | 2009-11-02 | "Austin, TX"  | "We're a responsible, easygoing couple who enjoy Austin's friendly atmosphere, good food, and great music. We enjoy gardening, reading, travel, and renovating our hundred-year-old home bit by bit. <br /> Our best times in Austin are on bikes--you can see a lot, get some sun, and get around downtown without the hassle of a car."                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | within a few hours | 100%               | 93%                  | t                 | https://a0.muscache.com/im/users/50793/profile_pic/1368134658/original.jpg?aki_policy=profile_small        | https://a0.muscache.com/im/users/50793/profile_pic/1368134658/original.jpg?aki_policy=profile_x_medium        | East Downtown      | 2                   | 2                         | "['email', 'phone']"               | t                    | t                      | "Austin, Texas, United States" | 78702                  |                              | 30.26098 | -97.73072 | Entire home          | Entire home/apt | 3            |           | 2 baths        |          | 2    | []        | $123.00 | 30             | 180            | 30                     | 30                     | 180                    | 180                    | 30.0                   | 180.0                  |                  | t                | 0               | 0               | 0               | 201              | 2023-12-17            | 18                | 1                     | 0                      | 2011-03-16   | 2023-06-19  | 5.0                  | 4.94                   | 4.94                      | 5.0                   | 5.0                         | 5.0                    | 4.94                |         | f                | 2                              | 2                                           | 0                                            | 0                                           | 0.12              |
| 18258  | https://www.airbnb.com/rooms/18258  | 20231215200307 | 2023-12-16   | previous scrape | Bungalow in Austin · ★5.0 · 3 bedrooms · 2 beds · 2 baths   |             | Sweet Briarcliff                                                                                                                                                                                                                                                                                                                                                                                                        | https://a0.muscache.com/pictures/miso/Hosting-18258/original/9f5cc881-7c72-4edd-824b-c52d0fde7378.jpeg | 39458   | https://www.airbnb.com/users/show/39458   | Billy          | 2009-09-18 | "Austin, TX"  | "Hi, <br /> My name is billyb.  I love history, travel, bicycle touring, reading and spicy food. I've been a digital nomad since 2009, and a happy Airbnb user since the first days of the platform. <br /> Meeting people and learning about their culture fills me up, inspires my belief in people, and animates my work."                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | within an hour     | 100%               | 96%                  | f                 | https://a0.muscache.com/im/pictures/user/af313631-6757-4196-b48c-7aeb192ae813.jpg?aki_policy=profile_small | https://a0.muscache.com/im/pictures/user/af313631-6757-4196-b48c-7aeb192ae813.jpg?aki_policy=profile_x_medium |                    | 1                   | 4                         | "['email', 'phone']"               | t                    | t                      | "Austin, Texas, United States" | 78745                  |                              | 30.19756 | -97.78754 | Entire bungalow      | Entire home/apt | 2            |           | 2 baths        |          | 2    | []        | $100.00 | 3              | 30             | 3                      | 3                      | 1125                   | 1125                   | 3.0                    | 1125.0                 |                  | t                | 0               | 0               | 0               | 0                | 2023-12-16            | 20                | 18                    | 1                      | 2022-10-25   | 2023-11-22  | 5.0                  | 5.0                    | 5.0                       | 5.0                   | 5.0                         | 4.6                    | 4.95                |         | f                | 1                              | 1                                           | 0                                            | 0                                           | 1.44              |
| 22828  | https://www.airbnb.com/rooms/22828  | 20231215200307 | 2023-12-16   | city scrape     | Guesthouse in Austin · ★4.94 · 1 bedroom · 1 bed · 1 bath   |             | "wikipedia: East_Riverside-Oltorf,_Austin,_Texas"                                                                                                                                                                                                                                                                                                                                                                       | https://a0.muscache.com/pictures/miso/Hosting-22828/original/91072e92-a641-4c30-85ee-4b527c6ccac8.jpeg | 56488   | https://www.airbnb.com/users/show/56488   | David          | 2009-11-22 | "Austin, TX"  | "Wyoming native living in Austin since 1996. I like to garden, read, cook, and work on DIY projects."                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | within a few hours | 100%               | 50%                  | f                 | https://a0.muscache.com/im/users/56488/profile_pic/1281061774/original.jpg?aki_policy=profile_small        | https://a0.muscache.com/im/users/56488/profile_pic/1281061774/original.jpg?aki_policy=profile_x_medium        | East Riverside     | 1                   | 1                         | "['email', 'phone']"               | t                    | t                      | "Austin, Texas, United States" | 78741                  |                              | 30.23614 | -97.73225 | Entire guesthouse    | Entire home/apt | 2            |           | 1 bath         |          | 1    | []        | $58.00  | 30             | 365            | 30                     | 30                     | 365                    | 365                    | 30.0                   | 365.0                  |                  | t                | 14              | 14              | 20              | 281              | 2023-12-16            | 51                | 1                     | 0                      | 2010-03-16   | 2023-08-15  | 4.94                 | 5.0                    | 4.98                      | 5.0                   | 5.0                         | 4.78                   | 4.87                |         | f                | 1                              | 1                                           | 0                                            | 0                                           | 0.30              |
| 22982  | https://www.airbnb.com/rooms/22982  | 20231215200307 | 2023-12-16   | city scrape     | Guesthouse in Austin · ★4.91 · 2 bedrooms · 2 beds · 1 bath |             | "Clarksville is a small historic district west of Downtown. The low-key, pedestrian-friendly neighborhood is known for its modest bungalows and long-standing cafes and shops. Clarksville is bordered by a trendy commercial strip on Lamar Boulevard, as well as Treaty Oak, a state landmark.Our neighborhood is  approximately 2 miles to The Convention Center, Memorial Stadium, UT Austin campus, and downtown." | https://a0.muscache.com/pictures/2ca8dbf5-c53d-4e71-8604-27ea2fae6c8b.jpg                              | 89031   | https://www.airbnb.com/users/show/89031   | Gina           | 2010-03-06 | "Austin, TX"  | "My husband Ken and I are currently living in Largo, FL on the Gulf coast. I am a chef, gardener, and Mama of 3 adult children. We have vacation rentals in Austin and Indian Rocks Beach. If you have any questions about my listings, please feel free to reach out to me. <br /> Food , Fun, Life, Love!"                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | within a few hours | 100%               | 98%                  | t                 | https://a0.muscache.com/im/users/89031/profile_pic/1297172680/original.jpg?aki_policy=profile_small        | https://a0.muscache.com/im/users/89031/profile_pic/1297172680/original.jpg?aki_policy=profile_x_medium        | Clarksville        | 3                   | 5                         | "['email', 'phone']"               | t                    | t                      | "Austin, Texas, United States" | 78703                  |                              | 30.28074 | -97.75381 | Entire guesthouse    | Entire home/apt | 4            |           | 1 bath         |          | 2    | []        | $250.00 | 30             | 120            | 30                     | 30                     | 120                    | 120                    | 30.0                   | 120.0                  |                  | t                | 29              | 59              | 89              | 269              | 2023-12-16            | 168               | 3                     | 0                      | 2010-03-16   | 2023-10-23  | 4.91                 | 4.93                   | 4.97                      | 4.96                  | 4.9                         | 4.88                   | 4.83                |         | f                | 1                              | 1                                           | 0                                            | 0                                           | 1.00              |
| 40285  | https://www.airbnb.com/rooms/40285  | 20231215200307 | 2023-12-16   | city scrape     | Home in Austin · ★4.92 · 2 bedrooms · 2 beds · 2 baths      |             | "Far West Boulevard is a 10 minute walk and has many eateries, H.E.B. grocery, Starbucks, and much more!"                                                                                                                                                                                                                                                                                                               | https://a0.muscache.com/pictures/522263/35fdf2cb_original.jpg                                          | 170787  | https://www.airbnb.com/users/show/170787  | Robbie         | 2010-07-18 | "Austin, TX"  | "I have lived in Austin for over 30yrs.  and enjoy all of the opportunities that this city has to offer.  The parks and hiking trails and all of the outdoor activities are my favorites!  I worked in the design field here in Austin for many years and raised my 2 children.  I am now working on becoming a photographer.  Austin is such a great city, I can hardly find enough time to do all the things it has to offer!!!"                                                                                                                                                                                                                                                                                                                                                                                                       | N/A                | N/A                | 100%                 | f                 | https://a0.muscache.com/im/users/170787/profile_pic/1279564185/original.jpg?aki_policy=profile_small       | https://a0.muscache.com/im/users/170787/profile_pic/1279564185/original.jpg?aki_policy=profile_x_medium       | Northwest Hills    | 1                   | 1                         | "['email', 'phone']"               | t                    | f                      | "Austin, Texas, United States" | 78731                  |                              | 30.35123 | -97.76207 | Entire home          | Entire home/apt | 4            |           | 2 baths        |          | 2    | []        | $450.00 | 2              | 30             | 2                      | 2                      | 30                     | 30                     | 2.0                    | 30.0                   |                  | t                | 0               | 0               | 0               | 245              | 2023-12-16            | 40                | 3                     | 0                      | 2011-02-28   | 2023-10-23  | 4.92                 | 4.95                   | 4.95                      | 4.97                  | 4.92                        | 4.92                   | 4.79                |         | f                | 1                              | 1                                           | 0                                            | 0                                           | 0.26              |
| 47572  | https://www.airbnb.com/rooms/47572  | 20231215200307 | 2023-12-16   | city scrape     | Home in Austin · ★5.0 · 1 bedroom · 1 bed · 1 shared bath   |             | "It is a quiet street with few kids.  The surrounding kids are usually in by 8 pm.   Most kids are in by 8 pm.  It is quiet even on weekends.  Because I am single, I do have an alarm system and security cameras. Coffee shops and taco stands are nearby.  Restaurants are just up the street and so is grocery."                                                                                                    | https://a0.muscache.com/pictures/miso/Hosting-47572/original/72f9bbbb-f9eb-4fba-bca3-0b31d2fa0d0f.jpeg | 215917  | https://www.airbnb.com/users/show/215917  | Belinda        | 2010-08-28 | "Austin, TX"  | I am a single female with 2 well-behaved Yorkies who do not shed and are clean and well-behaved. Live in a nice and quaint home that has a good feel.  I work out of my home as a design consultant.  Non-smoker.  Am a world traveler and still desire to experience new places and adventures.  I am social but will respect your privacy.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             | within a few hours | 100%               | 100%                 | t                 | https://a0.muscache.com/im/users/215917/profile_pic/1283053539/original.jpg?aki_policy=profile_small       | https://a0.muscache.com/im/users/215917/profile_pic/1283053539/original.jpg?aki_policy=profile_x_medium       |                    | 1                   | 1                         | "['email', 'phone', 'work_email']" | t                    | t                      | "Austin, Texas, United States" | 78758                  |                              | 30.37783 | -97.70749 | Private room in home | Private room    | 1            |           | 1 shared bath  |          | 1    | []        | $43.00  | 30             | 120            | 30                     | 30                     | 120                    | 120                    | 30.0                   | 120.0                  |                  | t                | 14              | 36              | 50              | 276              | 2023-12-16            | 9                 | 2                     | 0                      | 2019-03-19   | 2023-11-02  | 5.0                  | 5.0                    | 5.0                       | 5.0                   | 5.0                         | 5.0                    | 5.0                 |         | f                | 1                              | 0                                           | 1                                            | 0                                           | 0.16              |
| 50318  | https://www.airbnb.com/rooms/50318  | 20231215200307 | 2023-12-16   | city scrape     | Condo in Austin · ★4.88 · 2 bedrooms · 3 beds · 1 bath      |             | This neighborhood is very very mellow and quiet.  It's close to EVERYTHING.  Many things are walkable and it's also close to several buslines.  If you are driving all over town a lot it's also right in the center of town and right smack in between the two main highways going north and south.                                                                                                                    | https://a0.muscache.com/pictures/25719098/a118d875_original.jpg                                        | 12409   | https://www.airbnb.com/users/show/12409   | Flip           | 2009-04-06 | "Austin, TX"  | I LOVE AIRBNB!  I've been a host and traveler on airbnb for 9 years now and have loved every single person I have met on the way!  I started out renting my tiny handmade house in South Austin and now I rent adorable and conveniently located spots in Central Austin.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | within a day       | 100%               | 83%                  | t                 | https://a0.muscache.com/im/pictures/user/6514dabb-e21b-4ad1-9cf1-f7f22943e983.jpg?aki_policy=profile_small | https://a0.muscache.com/im/pictures/user/6514dabb-e21b-4ad1-9cf1-f7f22943e983.jpg?aki_policy=profile_x_medium | West Campus        | 2                   | 30                        | "['email', 'phone']"               | t                    | t                      | "Austin, Texas, United States" | 78705                  |                              | 30.28588 | -97.75145 | Entire condo         | Entire home/apt | 2            |           | 1 bath         |          | 3    | []        | $100.00 | 30             | 1125           | 30                     | 30                     | 1125                   | 1125                   | 30.0                   | 1125.0                 |                  | t                | 30              | 60              | 90              | 365              | 2023-12-16            | 34                | 2                     | 0                      | 2010-10-25   | 2023-07-18  | 4.88                 | 4.74                   | 4.74                      | 5.0                   | 4.97                        | 4.84                   | 4.81                |         | f                | 2                              | 2                                           | 0                                            | 0                                           | 0.21              |
| 57187  | https://www.airbnb.com/rooms/57187  | 20231215200307 | 2023-12-17   | city scrape     | Guesthouse in Austin · ★4.92 · 1 bedroom · 3 beds · 1 bath  |             | "The neighborhood is filled with homes from as early 1900's to modern remodels. All the homes on my street started as 1960's Ranch style. Today you never know what you will find next door or a block away.  Regardless, we are truly a neighborhood that has real neighbors who know each other and walk, bike, drive the hood."                                                                                      | https://a0.muscache.com/pictures/4994fc87-b9fe-401f-ad9e-3f9b41f38631.jpg                              | 272156  | https://www.airbnb.com/users/show/272156  | Lois           | 2010-10-27 | "Austin, TX"  | Professional Intuitive and relationship advice columnist.. Lived here since 1981. I know my way around Austin and don't mind telling you all about it. Art car artist since 1999. I have decorated 5 cars and you will probably see my car in the driveway when you arrive. Weird home owner. Doing my best to keep Austin weird.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | within an hour     | 100%               | 99%                  | t                 | https://a0.muscache.com/im/users/272156/profile_pic/1379040500/original.jpg?aki_policy=profile_small       | https://a0.muscache.com/im/users/272156/profile_pic/1379040500/original.jpg?aki_policy=profile_x_medium       | Zilker             | 2                   | 2                         | "['email', 'phone']"               | t                    | t                      | "Austin, Texas, United States" | 78704                  |                              | 30.25756 | -97.76995 | Entire guesthouse    | Entire home/apt | 6            |           | 1 bath         |          | 3    | []        | $90.00  | 1              | 15             | 1                      | 4                      | 15                     | 15                     | 1.4                    | 15.0                   |                  | t                | 23              | 50              | 78              | 346              | 2023-12-17            | 1016              | 76                    | 4                      | 2011-01-02   | 2023-12-07  | 4.92                 | 4.94                   | 4.93                      | 4.96                  | 4.96                        | 4.95                   | 4.82                |         | f                | 2                              | 2                                           | 0                                            | 0                                           | 6.44              |
| 69303  | https://www.airbnb.com/rooms/69303  | 20231215200307 | 2023-12-16   | city scrape     | Condo in Austin · ★4.96 · 1 bedroom · 2 beds · 1.5 baths    |             | "Located on a quiet street in 78704, which is one of the city's best neighborhoods. It's a short walk to Barton Springs pool, the botanical gardens, and Zilker Park. An abundance of food trucks, restaurants, and bike rentals is less than a mile away. Just two miles from downtown. Convenient to everything you might want to do in Austin."                                                                      | https://a0.muscache.com/pictures/48c56787-d071-4712-859d-7fe5972ff5ef.jpg                              | 272156  | https://www.airbnb.com/users/show/272156  | Lois           | 2010-10-27 | "Austin, TX"  | Professional Intuitive and relationship advice columnist.. Lived here since 1981. I know my way around Austin and don't mind telling you all about it. Art car artist since 1999. I have decorated 5 cars and you will probably see my car in the driveway when you arrive. Weird home owner. Doing my best to keep Austin weird.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | within an hour     | 100%               | 99%                  | t                 | https://a0.muscache.com/im/users/272156/profile_pic/1379040500/original.jpg?aki_policy=profile_small       | https://a0.muscache.com/im/users/272156/profile_pic/1379040500/original.jpg?aki_policy=profile_x_medium       | Zilker             | 2                   | 2                         | "['email', 'phone']"               | t                    | t                      | "Austin, Texas, United States" | 78704                  |                              | 30.26146 | -97.77276 | Entire condo         | Entire home/apt | 4            |           | 1.5 baths      |          | 2    | []        | $143.00 | 1              | 90             | 1                      | 30                     | 120                    | 1125                   | 1.6                    | 1118.1                 |                  | t                | 21              | 41              | 65              | 321              | 2023-12-16            | 232               | 28                    | 1                      | 2011-04-24   | 2023-11-19  | 4.96                 | 4.95                   | 4.96                      | 5.0                   | 4.99                        | 4.95                   | 4.83                |         | t                | 2                              | 2                                           | 0                                            | 0                                           | 1.51              |
| 69810  | https://www.airbnb.com/rooms/69810  | 20231215200307 | 2023-12-16   | previous scrape | Guesthouse in Austin · ★4.98 · 1 bedroom · 1 bed · 1 bath   |             | "Located in the cool Dawson area, about two miles south of downtown, the house is a short walk to coffee shops, a rock-climbing gym, and a variety of eateries. Public transportation is nearby."                                                                                                                                                                                                                       | https://a0.muscache.com/pictures/65d0d66a-9765-4d47-8242-1103ff0f7e34.jpg                              | 82762   | https://www.airbnb.com/users/show/82762   | Dolina         | 2010-02-18 | "Austin, TX"  | "My husband and I spent a year traveling the world in 2008. We stayed in literally hundreds of places. Some were great and some were awful, but what the great ones all had in common was a welcoming host that helped us feel more like locals. Airbnb gives us the opportunity to welcome other travelers to our part of the world."                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | N/A                | N/A                | N/A                  | f                 | https://a0.muscache.com/im/users/82762/profile_pic/1295303004/original.jpg?aki_policy=profile_small        | https://a0.muscache.com/im/users/82762/profile_pic/1295303004/original.jpg?aki_policy=profile_x_medium        | Dawson             | 1                   | 1                         | "['email', 'phone']"               | t                    | t                      | "Austin, Texas, United States" | 78704                  |                              | 30.2309  | -97.76619 | Entire guesthouse    | Entire home/apt | 2            |           | 1 bath         |          | 1    | []        |         | 2              | 730            | 2                      | 2                      | 1125                   | 1125                   | 2.0                    | 1125.0                 |                  |                  | 0               | 0               | 0               | 0                | 2023-12-16            | 445               | 0                     | 0                      | 2011-03-02   | 2022-03-08  | 4.98                 | 4.98                   | 5.0                       | 4.99                  | 4.99                        | 4.8                    | 4.95                |         | f                | 1                              | 1                                           | 0                                            | 0                                           | 2.86              |
| 218402 | https://www.airbnb.com/rooms/218402 | 20231215200307 | 2023-12-16   | city scrape     | Home in Austin · ★4.74 · 1 bedroom · 1 bed · 1 private bath |             | "Austinites think my neighborhood is WAAAY out, but really only 20 minutes to downtown or North Austin.  It takes 35-45 minutes for South Austin and far west destinations.  <br /> The area does feel like being in the boonies because the route from U.S. 290 includes about 2 miles of rural-looking road. It really adds a relaxing feel to commute."                                                              | https://a0.muscache.com/pictures/29960604/c568c32a_original.jpg                                        | 1129520 | https://www.airbnb.com/users/show/1129520 | Paulette       | 2011-09-08 | "Austin, TX"  | "I'm a grandmother still actively engaged with work and community activities.  I like making new friends and sharing my home. I'm somewhat vegetarian, enjoy gardening and singing in the church choir.  Would love to see more movies and plays. <br /> My new adorable dog likes to play with my roommates - after she gets to know them.  Otherwise she pretty much sticks to her favorite places and is sequestered in my room when I'm gone.  Sophia is a pretty chiquaqua and is not the grey dog in the picture. <br /> I work from home, so I the ideal guest has his or her own daytime activities out of the house.  There's an extra bedroom with a desk that can be rented at extra cost if the person chooses to work from home."                                                                                           | within a day       | 100%               | 80%                  | f                 | https://a0.muscache.com/im/pictures/user/d08f5942-3739-4c34-a965-4b72a74078ea.jpg?aki_policy=profile_small | https://a0.muscache.com/im/pictures/user/d08f5942-3739-4c34-a965-4b72a74078ea.jpg?aki_policy=profile_x_medium |                    | 1                   | 2                         | "['email', 'phone']"               | t                    | t                      | "Austin, Texas, United States" | 78754                  |                              | 30.36145 | -97.64397 | Private room in home | Private room    | 1            |           | 1 private bath |          | 1    | []        | $30.00  | 28             | 365            | 28                     | 28                     | 365                    | 365                    | 28.0                   | 365.0                  |                  | t                | 2               | 7               | 7               | 252              | 2023-12-16            | 29                | 2                     | 0                      | 2011-11-17   | 2023-09-24  | 4.74                 | 4.83                   | 4.93                      | 4.9                   | 4.76                        | 4.66                   | 4.79                |         | f                | 1                              | 0                                           | 1                                            | 0                                           | 0.20              |
| 70367  | https://www.airbnb.com/rooms/70367  | 20231215200307 | 2023-12-16   | city scrape     | Rental unit in Austin · ★4.94 · 1 bedroom · 1 bed · 1 bath  |             | "NW Hills is 2,500 acres of hilly terrain and breathtaking panoramas of Austin. Easy access to Mopac (Loop 1) and Capital of Texas Hwy (360). It's an ideal place to call home as it's known for their safe, family-friendly neighborhoods, great shops and cafes, and secluded vibe."                                                                                                                                  | https://a0.muscache.com/pictures/465441/ce0fa94f_original.jpg                                          | 10983   | https://www.airbnb.com/users/show/10983   | Lynn           | 2009-03-22 | "Austin, TX"  | "Namaste! I'm a career coach, life purpose educator, yoga philosopher, wellness author, retreat facilitator, health foodie, neat freak, art & nature lover, and all-around happy person. I live part-time in Texas and part-time in Hawaii. When I'm away my hope is to share my sanctuary with others who also value peace, wellness, and cute animals."                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | N/A                | N/A                | N/A                  | f                 | https://a0.muscache.com/im/pictures/user/76930d83-8dcb-4a99-bf2b-d2dc2eb9d100.jpg?aki_policy=profile_small | https://a0.muscache.com/im/pictures/user/76930d83-8dcb-4a99-bf2b-d2dc2eb9d100.jpg?aki_policy=profile_x_medium | Bull Creek         | 1                   | 1                         | "['email', 'phone']"               | t                    | t                      | "Austin, Texas, United States" | 78731                  |                              | 30.37403 | -97.76096 | Entire rental unit   | Entire home/apt | 2            |           | 1 bath         |          | 1    | []        | $50.00  | 30             | 80             | 30                     | 30                     | 80                     | 80                     | 30.0                   | 80.0                   |                  | t                | 0               | 0               | 20              | 58               | 2023-12-16            | 18                | 0                     | 0                      | 2011-03-20   | 2013-06-01  | 4.94                 | 4.82                   | 4.82                      | 5.0                   | 4.94                        | 4.82                   | 4.65                |         | f                | 1                              | 1                                           | 0                                            | 0                                           | 0.12              |
| 70812  | https://www.airbnb.com/rooms/70812  | 20231215200307 | 2023-12-16   | city scrape     | Guesthouse in Austin · ★4.89 · 1 bedroom · 3 beds · 1 bath  |             | "We are the first block off of Congress.  Easy access to Tony Grocer and June's, Torchy's, etc."                                                                                                                                                                                                                                                                                                                        | https://a0.muscache.com/pictures/9cb23da9-de8b-4480-a314-e0b023066faf.jpg                              | 268988  | https://www.airbnb.com/users/show/268988  | Stephanie      | 2010-10-23 | "Austin, TX"  | "Stephanie and Michael wanted to live in walking distance of something.   We love our house and its location. From here we can walk to restaurants and coffee shops and all the rest of Austin comes to South Congress.  <br /> Our house is a great mix of a 1935 Craftsman  and a modern infusion of steel and concrete.   The two places we list on this site are the upstairs and downstairs of the former garage. <br /> Stephanie works in animal welfare and real estate and Michael is a Clean Energy Executive. mdbreen is his id on most social media sites. <br /> https://www.airbnb.com/locations/austin/south-congress <br /> Austin's Diviest Dive Bars, <br /> Mapped http://austin.eater.com/maps/austins-diviest-dive-bars-mapped via @EaterAustin"                                                                    | within a day       | 100%               | 67%                  | f                 | https://a0.muscache.com/im/users/268988/profile_pic/1331264658/original.jpg?aki_policy=profile_small       | https://a0.muscache.com/im/users/268988/profile_pic/1331264658/original.jpg?aki_policy=profile_x_medium       | South Congress     | 1                   | 2                         | "['email', 'phone']"               | t                    | t                      | "Austin, Texas, United States" | 78704                  |                              | 30.24648 | -97.74913 | Entire guesthouse    | Entire home/apt | 3            |           | 1 bath         |          | 3    | []        | $165.00 | 2              | 30             | 2                      | 2                      | 30                     | 30                     | 2.0                    | 30.0                   |                  | t                | 29              | 59              | 87              | 87               | 2023-12-16            | 181               | 7                     | 1                      | 2011-03-16   | 2023-12-03  | 4.89                 | 4.93                   | 4.9                       | 4.98                  | 4.92                        | 4.95                   | 4.81                |         | f                | 1                              | 1                                           | 0                                            | 0                                           | 1.17              |
| 219168 | https://www.airbnb.com/rooms/219168 | 20231215200307 | 2023-12-16   | previous scrape | Rental unit in Austin · ★4.88 · Studio · 1 bed · 1 bath     |             | "Despite its proximity to South Congress and the Madness of the Festivals, in 3 short blocks, you are away from everything and surrounded by nature in a safe and quiet neighborhood."                                                                                                                                                                                                                                  | https://a0.muscache.com/pictures/33667722/08bb5106_original.jpg                                        | 1134580 | https://www.airbnb.com/users/show/1134580 | Kalu           | 2011-09-09 | "Austin, TX"  | "i am local musician here in austin, love food from all cultures, reading, watching movies, traveling and surrounding myself with creative and passionate people. <br /> As a host, I want to make sure that you are absolutely comfortable with our home as well as the surroundings. <br /> "                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          | N/A                | N/A                | N/A                  | f                 | https://a0.muscache.com/im/users/1134580/profile_pic/1393440474/original.jpg?aki_policy=profile_small      | https://a0.muscache.com/im/users/1134580/profile_pic/1393440474/original.jpg?aki_policy=profile_x_medium      | Travis Heights     | 1                   | 1                         | "['email', 'phone']"               | t                    | t                      | "Austin, Texas, United States" | 78704                  |                              | 30.24519 | -97.74486 | Entire rental unit   | Entire home/apt | 2            |           | 1 bath         |          | 1    | []        |         | 2              | 60             | 2                      | 2                      | 60                     | 60                     | 2.0                    | 60.0                   |                  |                  | 0               | 0               | 0               | 0                | 2023-12-16            | 8                 | 0                     | 0                      | 2012-03-14   | 2016-10-09  | 4.88                 | 4.63                   | 4.5                       | 4.88                  | 4.75                        | 4.88                   | 4.88                |         | f                | 1                              | 1                                           | 0                                            | 0                                           | 0.06              |
| 72833  | https://www.airbnb.com/rooms/72833  | 20231215200307 | 2023-12-16   | previous scrape | Guesthouse in Austin · ★4.91 · 1 bedroom · 1 bed · 1 bath   |             | "Peaceful neighborhood street in central Austin near 35th Street and Mopac (Loop 1), five miles from downtown attractions such as SoCo and Barton Springs.  Close to Shoal Creek Greenbelt and bike routes."                                                                                                                                                                                                            | https://a0.muscache.com/pictures/miso/Hosting-72833/original/4fef19d6-a0a5-4af0-9d69-59a202521265.jpeg | 378744  | https://www.airbnb.com/users/show/378744  | Ellen And Andy | 2011-02-05 | "Austin, TX"  | "Easy-going couple, longtime residents of Austin, we love food, music, cocktails <br /> and the outdoors. Andy is into bicycles and sometimes rides his bike to work.  We are both legal professionals."                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | N/A                | N/A                | 100%                 | t                 | https://a0.muscache.com/im/users/378744/profile_pic/1377100724/original.jpg?aki_policy=profile_small       | https://a0.muscache.com/im/users/378744/profile_pic/1377100724/original.jpg?aki_policy=profile_x_medium       | Rosedale           | 1                   | 1                         | "['email', 'phone', 'work_email']" | t                    | t                      | "Austin, Texas, United States" | 78731                  |                              | 30.313   | -97.75066 | Entire guesthouse    | Entire home/apt | 2            |           | 1 bath         |          | 1    | []        |         | 3              | 60             | 3                      | 3                      | 1125                   | 1125                   | 3.0                    | 1125.0                 |                  |                  | 0               | 0               | 0               | 0                | 2023-12-16            | 413               | 3                     | 0                      | 2011-03-14   | 2023-03-26  | 4.91                 | 4.92                   | 4.9                       | 4.96                  | 4.96                        | 4.9                    | 4.91                |         | f                | 1                              | 1                                           | 0                                            | 0                                           | 2.66              |

I noticed that a few records in `neighbourhood` Austin (`"Austin, Texas, United States"`) were written incorrectly (e.g., `"Austin Texas, United, States"` (line 154), `"Austin , Texas, United States"` (line 7261), etc.), as shown below:

| id       | listing_url                           | scrape_id      | last_scraped | source      | name                                                        | ... | neighbourhood                   | neighbourhood_cleansed | neighbourhood_group_cleansed | ... |
|----------|---------------------------------------|----------------|--------------|-------------|-------------------------------------------------------------|-----|---------------------------------|------------------------|------------------------------|-----|
| 104386   | https://www.airbnb.com/rooms/104386   | 20231215200307 | 2023-12-17   | city scrape | Home in Austin Texas · ★4.97 · 2 bedrooms · 3 beds · 1 bath | ... | "Austin Texas, United States"   | 78704                  |                              | ... |
| 23696016 | https://www.airbnb.com/rooms/23696016 | 20231215200307 | 2023-12-16   | city scrape | Cottage in Austin  · ★4.74 · 1 bedroom · 1 bed · 1 bath     | ... | "Austin , Texas, United States" | 78734                  |                              | ... |

All these mistakes are corrected to `"Austin, Texas, United States"` using text editor as each of them has only one occurence when searching in VScode. Similar mistakes were not found in other value of `neighbourhoods`. The [munged dataset](./data/listings_clean.csv) was stored and used for following analysis in MongoDB.

## Analysis
1. show exactly two documents from the `listings` collection in any order
```javascript
db.listings.find().limit(2)
```
**Results**:
```javascript
[
  {
    _id: ObjectId('65dce1257e28b59b53921d63'),
    id: 5456,
    listing_url: 'https://www.airbnb.com/rooms/5456',
    scrape_id: Long('20231215200307'),
    last_scraped: '2023-12-16',
    source: 'city scrape',
    name: 'Guesthouse in Austin · ★4.84 · 1 bedroom · 2 beds · 1 bath',
    description: '',
    neighborhood_overview: 'My neighborhood is ideally located if you want to walk to bars and restaurants downtown, East 6th Street or Rainey Street.  The Convention Center is only 3 1/2 blocks away and a quick 10 minute walk. Whole foods store located 5 blks , easily walkable.',
    picture_url: 'https://a0.muscache.com/pictures/14084884/b5a35a84_original.jpg',
    host_id: 8028,
    host_url: 'https://www.airbnb.com/users/show/8028',
    host_name: 'Sylvia',
    host_since: '2009-02-16',
    host_location: 'Austin, TX',
    host_about: 'I am a licensed Real Estate Broker and owner of Armadillo Realty.  I attended The University of Texas at Austin and fell in love with the small town that it was back in 1979; I have been here every since.  I love the Art, Music and Film scene here in Austin.  There is so much natural beauty to enjoy as well. I especially enjoy Barton Springs Pool in the summertime along with the Zilker Hillside theater productions. SXSW, Austin City Limits Festival and the East Austin Art Studio Tour are among my favorite events. I also enjoy a sunset cruise on my canoe to Congress bridge to see the Mexican Freetail Bats come out for their nightly feeding.  ',
    host_response_time: 'within an hour',
    host_response_rate: '100%',
    host_acceptance_rate: '97%',
    host_is_superhost: 't',
    host_thumbnail_url: 'https://a0.muscache.com/im/users/8028/profile_pic/1329882962/original.jpg?aki_policy=profile_small',
    host_picture_url: 'https://a0.muscache.com/im/users/8028/profile_pic/1329882962/original.jpg?aki_policy=profile_x_medium',
    host_neighbourhood: 'East Downtown',
    host_listings_count: 1,
    host_total_listings_count: 4,
    host_verifications: "['email', 'phone']",
    host_has_profile_pic: 't',
    host_identity_verified: 't',
    neighbourhood: 'Austin, Texas, United States',
    neighbourhood_cleansed: 78702,
    neighbourhood_group_cleansed: '',
    latitude: 30.26057,
    longitude: -97.73441,
    property_type: 'Entire guesthouse',
    room_type: 'Entire home/apt',
    accommodates: 3,
    bathrooms: '',
    bathrooms_text: '1 bath',
    bedrooms: '',
    beds: 2,
    amenities: '[]',
    price: '$101.00',
    minimum_nights: 2,
    maximum_nights: 90,
    minimum_minimum_nights: 2,
    maximum_minimum_nights: 2,
    minimum_maximum_nights: 90,
    maximum_maximum_nights: 90,
    minimum_nights_avg_ntm: 2,
    maximum_nights_avg_ntm: 90,
    calendar_updated: '',
    has_availability: 't',
    availability_30: 21,
    availability_60: 51,
    availability_90: 74,
    availability_365: 330,
    calendar_last_scraped: '2023-12-16',
    number_of_reviews: 668,
    number_of_reviews_ltm: 47,
    number_of_reviews_l30d: 1,
    first_review: '2009-03-08',
    last_review: '2023-11-20',
    review_scores_rating: 4.84,
    review_scores_accuracy: 4.88,
    review_scores_cleanliness: 4.86,
    review_scores_checkin: 4.89,
    review_scores_communication: 4.83,
    review_scores_location: 4.73,
    review_scores_value: 4.79,
    license: '',
    instant_bookable: 'f',
    calculated_host_listings_count: 1,
    calculated_host_listings_count_entire_homes: 1,
    calculated_host_listings_count_private_rooms: 0,
    calculated_host_listings_count_shared_rooms: 0,
    reviews_per_month: 3.71
  },
  {
    _id: ObjectId('65dce1257e28b59b53921d64'),
    id: 5769,
    listing_url: 'https://www.airbnb.com/rooms/5769',
    scrape_id: Long('20231215200307'),
    last_scraped: '2023-12-16',
    source: 'previous scrape',
    name: 'Home in Austin · ★4.91 · 1 bedroom · 1 bed · 1 shared bath',
    description: '',
    neighborhood_overview: 'Quiet neighborhood with lots of trees and good neighbors.',
    picture_url: 'https://a0.muscache.com/pictures/23822033/ac946aff_original.jpg',
    host_id: 8186,
    host_url: 'https://www.airbnb.com/users/show/8186',
    host_name: 'Elizabeth',
    host_since: '2009-02-19',
    host_location: 'Austin, TX',
    host_about: "We're easygoing professionals that enjoy meeting new people.  I love martial arts, the outdoors, kayaking, live music, good food and positive people. I can converse in Spanish and can cook a mean Mexican dinner.",
    host_response_time: 'within an hour',
    host_response_rate: '100%',
    host_acceptance_rate: '88%',
    host_is_superhost: 't',
    host_thumbnail_url: 'https://a0.muscache.com/im/users/8186/profile_pic/1272556663/original.jpg?aki_policy=profile_small',
    host_picture_url: 'https://a0.muscache.com/im/users/8186/profile_pic/1272556663/original.jpg?aki_policy=profile_x_medium',
    host_neighbourhood: 'SW Williamson Co.',
    host_listings_count: 1,
    host_total_listings_count: 4,
    host_verifications: "['email', 'phone', 'work_email']",
    host_has_profile_pic: 't',
    host_identity_verified: 't',
    neighbourhood: 'Austin, Texas, United States',
    neighbourhood_cleansed: 78729,
    neighbourhood_group_cleansed: '',
    latitude: 30.45697,
    longitude: -97.78422,
    property_type: 'Private room in home',
    room_type: 'Private room',
    accommodates: 2,
    bathrooms: '',
    bathrooms_text: '1 shared bath',
    bedrooms: '',
    beds: 1,
    amenities: '[]',
    price: '',
    minimum_nights: 1,
    maximum_nights: 14,
    minimum_minimum_nights: 1,
    maximum_minimum_nights: 1,
    minimum_maximum_nights: 14,
    maximum_maximum_nights: 14,
    minimum_nights_avg_ntm: 1,
    maximum_nights_avg_ntm: 14,
    calendar_updated: '',
    has_availability: '',
    availability_30: 0,
    availability_60: 0,
    availability_90: 0,
    availability_365: 0,
    calendar_last_scraped: '2023-12-16',
    number_of_reviews: 294,
    number_of_reviews_ltm: 20,
    number_of_reviews_l30d: 2,
    first_review: '2010-04-10',
    last_review: '2023-12-07',
    review_scores_rating: 4.91,
    review_scores_accuracy: 4.9,
    review_scores_cleanliness: 4.87,
    review_scores_checkin: 4.91,
    review_scores_communication: 4.94,
    review_scores_location: 4.76,
    review_scores_value: 4.92,
    license: '',
    instant_bookable: 'f',
    calculated_host_listings_count: 1,
    calculated_host_listings_count_entire_homes: 0,
    calculated_host_listings_count_private_rooms: 1,
    calculated_host_listings_count_shared_rooms: 0,
    reviews_per_month: 1.76
  }
]
```
**Insights**:
+ Both listings first opened between 2009 and 2010.
+ `Home in Austin` is either smaller or more popular than `Guesthouse in Austin` as the former has no room available while the latter has plenty.

2. show exactly 10 documents in any order, but "prettyprint" in easier to read format, using the `pretty()` function.
```javascript
db.listings.find().limit(10).pretty()
```
**Results** (first 3 documents):
```javascript
[
  {
    _id: ObjectId('65dbea907e28b59b5391d83f'),
    id: 5456,
    listing_url: 'https://www.airbnb.com/rooms/5456',
    scrape_id: Long('20231215200307'),
    last_scraped: '2023-12-16',
    source: 'city scrape',
    name: 'Guesthouse in Austin · ★4.84 · 1 bedroom · 2 beds · 1 bath',
    description: '',
    neighborhood_overview: 'My neighborhood is ideally located if you want to walk to bars and restaurants downtown, East 6th Street or Rainey Street.  The Convention Center is only 3 1/2 blocks away and a quick 10 minute walk. Whole foods store located 5 blks , easily walkable.',
    picture_url: 'https://a0.muscache.com/pictures/14084884/b5a35a84_original.jpg',
    host_id: 8028,
    host_url: 'https://www.airbnb.com/users/show/8028',
    host_name: 'Sylvia',
    host_since: '2009-02-16',
    host_location: 'Austin, TX',
    host_about: 'I am a licensed Real Estate Broker and owner of Armadillo Realty.  I attended The University of Texas at Austin and fell in love with the small town that it was back in 1979; I have been here every since.  I love the Art, Music and Film scene here in Austin.  There is so much natural beauty to enjoy as well. I especially enjoy Barton Springs Pool in the summertime along with the Zilker Hillside theater productions. SXSW, Austin City Limits Festival and the East Austin Art Studio Tour are among my favorite events. I also enjoy a sunset cruise on my canoe to Congress bridge to see the Mexican Freetail Bats come out for their nightly feeding.  ',
    host_response_time: 'within an hour',
    host_response_rate: '100%',
    host_acceptance_rate: '97%',
    host_is_superhost: 't',
    host_thumbnail_url: 'https://a0.muscache.com/im/users/8028/profile_pic/1329882962/original.jpg?aki_policy=profile_small',
    host_picture_url: 'https://a0.muscache.com/im/users/8028/profile_pic/1329882962/original.jpg?aki_policy=profile_x_medium',
    host_neighbourhood: 'East Downtown',
    host_listings_count: 1,
    host_total_listings_count: 4,
    host_verifications: "['email', 'phone']",
    host_has_profile_pic: 't',
    host_identity_verified: 't',
    neighbourhood: 'Austin, Texas, United States',
    neighbourhood_cleansed: 78702,
    neighbourhood_group_cleansed: '',
    latitude: 30.26057,
    longitude: -97.73441,
    property_type: 'Entire guesthouse',
    room_type: 'Entire home/apt',
    accommodates: 3,
    bathrooms: '',
    bathrooms_text: '1 bath',
    bedrooms: '',
    beds: 2,
    amenities: '[]',
    price: '$101.00',
    minimum_nights: 2,
    maximum_nights: 90,
    minimum_minimum_nights: 2,
    maximum_minimum_nights: 2,
    minimum_maximum_nights: 90,
    maximum_maximum_nights: 90,
    minimum_nights_avg_ntm: 2,
    maximum_nights_avg_ntm: 90,
    calendar_updated: '',
    has_availability: 't',
    availability_30: 21,
    availability_60: 51,
    availability_90: 74,
    availability_365: 330,
    calendar_last_scraped: '2023-12-16',
    number_of_reviews: 668,
    number_of_reviews_ltm: 47,
    number_of_reviews_l30d: 1,
    first_review: '2009-03-08',
    last_review: '2023-11-20',
    review_scores_rating: 4.84,
    review_scores_accuracy: 4.88,
    review_scores_cleanliness: 4.86,
    review_scores_checkin: 4.89,
    review_scores_communication: 4.83,
    review_scores_location: 4.73,
    review_scores_value: 4.79,
    license: '',
    instant_bookable: 'f',
    calculated_host_listings_count: 1,
    calculated_host_listings_count_entire_homes: 1,
    calculated_host_listings_count_private_rooms: 0,
    calculated_host_listings_count_shared_rooms: 0,
    reviews_per_month: 3.71
  },
  {
    _id: ObjectId('65dbea907e28b59b5391d840'),
    id: 5769,
    listing_url: 'https://www.airbnb.com/rooms/5769',
    scrape_id: Long('20231215200307'),
    last_scraped: '2023-12-16',
    source: 'previous scrape',
    name: 'Home in Austin · ★4.91 · 1 bedroom · 1 bed · 1 shared bath',
    description: '',
    neighborhood_overview: 'Quiet neighborhood with lots of trees and good neighbors.',
    picture_url: 'https://a0.muscache.com/pictures/23822033/ac946aff_original.jpg',
    host_id: 8186,
    host_url: 'https://www.airbnb.com/users/show/8186',
    host_name: 'Elizabeth',
    host_since: '2009-02-19',
    host_location: 'Austin, TX',
    host_about: "We're easygoing professionals that enjoy meeting new people.  I love martial arts, the outdoors, kayaking, live music, good food and positive people. I can converse in Spanish and can cook a mean Mexican dinner.",
    host_response_time: 'within an hour',
    host_response_rate: '100%',
    host_acceptance_rate: '88%',
    host_is_superhost: 't',
    host_thumbnail_url: 'https://a0.muscache.com/im/users/8186/profile_pic/1272556663/original.jpg?aki_policy=profile_small',
    host_picture_url: 'https://a0.muscache.com/im/users/8186/profile_pic/1272556663/original.jpg?aki_policy=profile_x_medium',
    host_neighbourhood: 'SW Williamson Co.',
    host_listings_count: 1,
    host_total_listings_count: 4,
    host_verifications: "['email', 'phone', 'work_email']",
    host_has_profile_pic: 't',
    host_identity_verified: 't',
    neighbourhood: 'Austin, Texas, United States',
    neighbourhood_cleansed: 78729,
    neighbourhood_group_cleansed: '',
    latitude: 30.45697,
    longitude: -97.78422,
    property_type: 'Private room in home',
    room_type: 'Private room',
    accommodates: 2,
    bathrooms: '',
    bathrooms_text: '1 shared bath',
    bedrooms: '',
    beds: 1,
    amenities: '[]',
    price: '',
    minimum_nights: 1,
    maximum_nights: 14,
    minimum_minimum_nights: 1,
    maximum_minimum_nights: 1,
    minimum_maximum_nights: 14,
    maximum_maximum_nights: 14,
    minimum_nights_avg_ntm: 1,
    maximum_nights_avg_ntm: 14,
    calendar_updated: '',
    has_availability: '',
    availability_30: 0,
    availability_60: 0,
    availability_90: 0,
    availability_365: 0,
    calendar_last_scraped: '2023-12-16',
    number_of_reviews: 294,
    number_of_reviews_ltm: 20,
    number_of_reviews_l30d: 2,
    first_review: '2010-04-10',
    last_review: '2023-12-07',
    review_scores_rating: 4.91,
    review_scores_accuracy: 4.9,
    review_scores_cleanliness: 4.87,
    review_scores_checkin: 4.91,
    review_scores_communication: 4.94,
    review_scores_location: 4.76,
    review_scores_value: 4.92,
    license: '',
    instant_bookable: 'f',
    calculated_host_listings_count: 1,
    calculated_host_listings_count_entire_homes: 0,
    calculated_host_listings_count_private_rooms: 1,
    calculated_host_listings_count_shared_rooms: 0,
    reviews_per_month: 1.76
  },
  {
    _id: ObjectId('65dbea907e28b59b5391d841'),
    id: 6413,
    listing_url: 'https://www.airbnb.com/rooms/6413',
    scrape_id: Long('20231215200307'),
    last_scraped: '2023-12-16',
    source: 'previous scrape',
    name: 'Guesthouse in Austin · ★4.97 · Studio · 1 bed · 1 bath',
    description: '',
    neighborhood_overview: "Travis Heights is one of the oldest neighborhoods in Austin. Our house was built in 1937. We rebuilt the apartment in 2009 (well, finished and furnished it for rental then). From the studio it's a pretty easy 1-mile walk through the neighborhood to all the shops and restaurants on South Congress.",
    picture_url: 'https://a0.muscache.com/pictures/miso/Hosting-6413/original/029304da-074c-4fce-bf9f-48a3c90d6283.jpeg',
    host_id: 13879,
    host_url: 'https://www.airbnb.com/users/show/13879',
    host_name: 'Todd',
    host_since: '2009-04-17',
    host_location: 'Austin, TX',
    host_about: "We're a young family that likes to travel, we just don't get to enough. So we live vicariously through our visiting guests. \n" +
      '\n' +
      "We run this little vacation rental apartment ourselves. As mentioned in the listing, it's located on our property. It's an above garage apartment that is completely separate from our home. We like to think it's a bit European to share our place with guests. We're very sensitive to guests' needs and give you plenty of space. We're happy to answer any questions about Austin, help you around town, make suggestions, and more if you'd like. We've lived in Austin for about 20 years and have been renting the studio for more than nine years and make improvements as we grow with it. Thank you for considering our place.\n" +
      '\n' +
      'PS. No, our profile pic was not taken in Austin:)',
    host_response_time: 'N/A',
    host_response_rate: 'N/A',
    host_acceptance_rate: '100%',
    host_is_superhost: 'f',
    host_thumbnail_url: 'https://a0.muscache.com/im/pictures/user/4f35ef11-7f37-45cf-80da-f914a6d5f451.jpg?aki_policy=profile_small',
    host_picture_url: 'https://a0.muscache.com/im/pictures/user/4f35ef11-7f37-45cf-80da-f914a6d5f451.jpg?aki_policy=profile_x_medium',
    host_neighbourhood: 'Travis Heights',
    host_listings_count: 1,
    host_total_listings_count: 1,
    host_verifications: "['email', 'phone']",
    host_has_profile_pic: 't',
    host_identity_verified: 't',
    neighbourhood: 'Austin, Texas, United States',
    neighbourhood_cleansed: 78704,
    neighbourhood_group_cleansed: '',
    latitude: 30.24885,
    longitude: -97.73587,
    property_type: 'Entire guesthouse',
    room_type: 'Entire home/apt',
    accommodates: 2,
    bathrooms: '',
    bathrooms_text: '1 bath',
    bedrooms: '',
    beds: 1,
    amenities: '[]',
    price: '',
    minimum_nights: 30,
    maximum_nights: 90,
    minimum_minimum_nights: 30,
    maximum_minimum_nights: 30,
    minimum_maximum_nights: 90,
    maximum_maximum_nights: 90,
    minimum_nights_avg_ntm: 30,
    maximum_nights_avg_ntm: 90,
    calendar_updated: '',
    has_availability: '',
    availability_30: 0,
    availability_60: 0,
    availability_90: 0,
    availability_365: 0,
    calendar_last_scraped: '2023-12-16',
    number_of_reviews: 120,
    number_of_reviews_ltm: 0,
    number_of_reviews_l30d: 0,
    first_review: '2009-12-14',
    last_review: '2022-10-17',
    review_scores_rating: 4.97,
    review_scores_accuracy: 4.99,
    review_scores_cleanliness: 4.99,
    review_scores_checkin: 4.99,
    review_scores_communication: 4.98,
    review_scores_location: 4.87,
    review_scores_value: 4.93,
    license: '',
    instant_bookable: 'f',
    calculated_host_listings_count: 1,
    calculated_host_listings_count_entire_homes: 1,
    calculated_host_listings_count_private_rooms: 0,
    calculated_host_listings_count_shared_rooms: 0,
    reviews_per_month: 0.7
  },
  /* Following documents... */
]
```
**Insights**:
+ `"Guesthouse in Austin"` with id `6413` requires a minimum booking of at least `30` nights.
+ `"Guesthouse in Austin"` with id `6413` has an `host_acceptance_rate` of `100%`.
+ The two `"Guesthouse in Austin"` might be in the same apartment building as the have very close latitude (around `30.2`) and longitude (around `-97.7`).

3. choose two hosts (by refering to their `host_id` values) who are superhosts (available in the `host_is_superhost` field), and show all of the listings offered by both of the two hosts
   - only show the `name`, `price`, `neighbourhood`, `host_name`, and `host_is_superhost` for each result
```javascript
db.listings.find(
    { 
        // Two hosts who are superhosts.
        host_id: {
            $in: [
                8028, 
                14156
            ]
        }
    }, 
    { 
        _id: 0, 
        "name": 1, 
        "price": 1, 
        "neighbourhood": 1, 
        "host_name": 1, 
        "host_is_superhost": 1
    }
)
```
**Results**:
```javascript
[
  {
    name: 'Guesthouse in Austin · ★4.84 · 1 bedroom · 2 beds · 1 bath',
    host_name: 'Sylvia',
    host_is_superhost: 't',
    neighbourhood: 'Austin, Texas, United States',
    price: '$101.00'
  },
  {
    name: 'Guesthouse in Austin · ★4.97 · 1 bedroom · 2 beds · 1 bath',
    host_name: 'Amy',
    host_is_superhost: 't',
    neighbourhood: 'Austin, Texas, United States',
    price: '$159.00'
  }
]
```
**Insights**:
+ Both hosts share one building name `"Guesthouse in Austin"`.
+ Both listings have similar designs: `"1 bedroom · 2 beds · 1 bath"`.

4. find all the unique `host_name` values
```javascript
db.listings.distinct("host_name")
```
**Results** (first 3 results):
```javascript
[
  NaN,                 '',                      '3 Little Birds',
  /* Following `host_name` values... */
]
```
**Insights**:
+ The system may have incorrect field setup as `NaN` (i.e., Not a Number) is a number type while all other `host_name` are strings. (Note that the corresponding row is still valid as other fields still have valid data).
+ The results might be based on the value of each character, as `''` appears before `'3 Little Birds'`, and the latter appears before `host_name` starts with `A`.

5. find all of the places that have more than 2 `beds` in a neighborhood of your choice (referred to as either the `neighborhood` or `neighbourhood_group_cleansed` fields in the data file), ordered by `review_scores_rating` descending
   - only show the `name`, `beds`, `review_scores_rating`, and `price`
   - if your data set only has blanks for all the neighborhood-related fields, or only one neighborhood value in all documents, you may pick another field to filter by - include an explanation and justification for this in your report.
   - if you run out of memory for this query, try filtering `review_scores_rating` that aren't empty (`$ne`); and lastly, if there's still an issue, you can set the `beds` to match exactly 2.
```javascript
db.listings.find(
    {
        "neighbourhood": "Sunset Valley, Texas, United States", 
        "beds": { $gt: 2 }
    }, 
    {
        _id: 0, 
        "name": 1, 
        "beds": 1, 
        "review_scores_rating": 1, 
        "price": 1
    }
).sort({ "review_scores_rating": -1 })
```
**Results** (first 3 documents):
```javascript
[
  {
    name: 'Villa in Sunset Valley · ★5.0 · 4 bedrooms · 8 beds · 4 baths',
    beds: 8,
    price: '$1,179.00',
    review_scores_rating: 5
  },
  {
    name: 'Home in Sunset Valley · ★5.0 · 4 bedrooms · 5 beds · 3 baths',
    beds: 5,
    price: '$190.00',
    review_scores_rating: 5
  },
  {
    name: 'Home in Sunset Valley · ★5.0 · 4 bedrooms · 6 beds · 4 baths',
    beds: 6,
    price: '$552.00',
    review_scores_rating: 5
  },
  /* Following documents... */
]
```
**Insights**:
+ The listings shown here have very large rooms with at least 4 bedrooms, 5 beds, and 3 baths.
+ For the listings shown here, there must be at least 1 room that contains 2 beds, 1 bed not in bedroom as there are more beds than bedrooms.
+ Listings with high rating are not always expensive as the second listing shown here are much cheaper than the other two but with perfect `review_scores_rating`, `5` out of 5.

6. show the number of listings per host
```javascript
db.listings.aggregate([
    {
        /* 
          Count the number of listings in the dataset that belongs
          to each host
        */
        $group: {
            _id: "$host_id", 
            numberOfListings: {
                $sum: 1
            }
        }
    }
])
```
**Results** (first 3 documents):
```javascript
[
  { _id: 221236783, numberOfListings: 1 },
  { _id: 2145939, numberOfListings: 3 },
  { _id: 124356835, numberOfListings: 1 },
  /* Following documents... */
]
```
**Insights**:
+ Most hosts have very few (less than `3`) listings.
+ Very few hosts have more than `5` listings.

7. find the average `review_scores_rating` per neighborhood, and only show those that are `4` or above, sorted in descending order of rating
   - if your data set only has blanks in the neighborhood-related fields, or only one neighborhood value in all documents, you may pick another field to break down the listings by - include an explanation and justification for this in your report.
```javascript
db.listings.aggregate([
    {
        // Group by `neighbourhood` and calculate average.
        $group: {
            _id: "$neighbourhood",
            avgReviewScoresRating: {
                $avg: "$review_scores_rating"
            }
        }
    }, 
    {
        // Select avarage greater than 4.
        $match: {
            avgReviewScoresRating: {
                $gte: 4
            }
        }
    }, 
    {
        // Sort result in decreasing order.
        $sort: {
            avgReviewScoresRating: -1
        }
    }
])
```
**Results** (first 3 documents):
```javascript
[
  {
    _id: 'East Austin, Texas, United States',
    avgReviewScoresRating: 5
  },
  { _id: 'Driftwood, Texas, United States', avgReviewScoresRating: 5 },
  {
    _id: 'Pflugerville, Texas, United States',
    avgReviewScoresRating: 5
  },
  /* Following documents... */
]
```
**Insights**:
+ Surprisingly, all nighbourhoods in the dataset has average `review_score_rating` greater than `4`, even greater than `4.7`.

## Extra-Credit

This assignment deserves extra credit because I used Python from **i6** to connect to the MongoDB database and performed the query mentioned in [instructions.md](./instructions.md).

### Setup
```python
import pymongo
import pprint # for printing results

password = ... # password not shown here

connection = pymongo.MongoClient("class-mongodb.cims.nyu.edu", 27017,
                                username="hl4963",
                                password=password,
                                authSource="hl4963")
collection = connection["hl4963"]["listings"]

# the collection variable will be a reference to your collection
docs = collection.find({}).limit(10) # get the first 10 documents
print(docs) # print line of reference to the result

for doc in docs:
    pprint.pprint(doc) # print each document
```

1. find all of the places that have more than 2 `beds` in a neighborhood of your choosing, ordered by `review_scores_rating` descending
   - only show the `name`, `beds`, `review_scores_rating`, and `price`
   - note that in `pymongo`, you'll have to quote all of your keys.
```python
citeria = {
    "neighbourhood": "Sunset Valley, Texas, United States", 
    "beds": { "$gt": 2 }
}

project = {
    "_id": 0, 
    "name": 1, 
    "beds": 1, 
    "review_scores_rating": 1, 
    "price": 1
}

order = [("review_scores_rating", -1)]

docs = collection.find(citeria, project).sort(order)

for doc in docs:
    pprint.pprint(doc) # print each document
```

**Results** (first 3 documents):
Notice that the query results is the same as that of query 5 shown above.
```python
{'beds': 8,
 'name': 'Villa in Sunset Valley · ★5.0 · 4 bedrooms · 8 beds · 4 baths',
 'price': '$1,179.00',
 'review_scores_rating': 5.0}
{'beds': 5,
 'name': 'Home in Sunset Valley · ★5.0 · 4 bedrooms · 5 beds · 3 baths',
 'price': '$190.00',
 'review_scores_rating': 5.0}
{'beds': 6,
 'name': 'Home in Sunset Valley · ★5.0 · 4 bedrooms · 6 beds · 4 baths',
 'price': '$552.00',
 'review_scores_rating': 5.0}
"""Following documents..."""
```