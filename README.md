# Final-Project-Statistical-Modelling-with-Python

## Project/Goals
to compile a responsive and reliable dataset from the three API with which I would be able to perform an accurate regression model that will show if my relationship hypothesis is correct. As I got into the thick of it , my goals evovlved from broader , aerial goals , to immediate specific goals like figuring out a way to request API from yelp after I had already used my quota up. ( I used a family member's email to create a a new account becasue I didnt have time for it to reset  ).  My goal was to have a greater quality and quantity of data which would allow for a better fit of the model (R squared value ) and at the same time not overfit. Since the data from both yelp and foruswuare was insuffiecnt , I could not achieve this goal , but nevertheless I gained more intuition for APIs , JSON files and coding with Python - which was really the purpose of this project.

##Process:
1) Api requests: chose a city for citybikes - picked Toronto where I live because knowing the context of the data helps ;)

2)parsing /extracting - used 'pprint' to format the json files , and JSON beautifier so I can understand the data to extract only the necessary information from it. In hinsight , I would extract more details to put into my dataframes but at that point I was nervous about my API limit and was not sure if looping through the response counts as an API call so I went with the bare minimum.

3)loading as csvs and merging - I created a dataframe for my foursquare , citybikes and yelp extracted data which I then saved as a csv . I then merged those dataframes using the common 'station_id' column they all had. the reason I saved these as a csv was becasue I was not sure if manipultating the dataframes / extracting info from them would count as an API call so just to be safe I saved them as CSVs and then uploaded them again and used that. 
4)EDA - used many visualizations using matplotlib and seaborn to conduct univariate ( for individual variables) and bivariate analysis ( exploring relationships between variables) . None of the visualizations wer compelling enough to assume a relationship exists - which was  true , the relationship was very weak. For the cleaning part - I didnt do much since my dataset was so small I kept everything as is . although I did notice duplicate Restaurant names for different stations , I did not remove them becasue my data set was too samll and it made contextual sense - the bikestations in Toronto are very densly placed so it would make sense for them to share a restaurant in their vicinity ( especially since I only got one name for each bikestaion - another learning curve) . This was validated by information I pulled from the city of Toronto (see slides for image). Regarding assessing data source reliability - I knew Yelp and Foursquare to be reliable data repositories so I did not spend any time on this aspect of quality assurance.

4)upload to sqlite - this part was fairly simple . all I did was upload the data to sqlite using the prooper code and setting a connection object and then ran a query to see if it worked. I had already merged my data as dataframes so I did not need to perform a SQL join

5)find problem and and hypothesis that will give insight to problem ie.problem = want to increase bike usage in Toronto . therefore the hypothesis I chose  determined if  there is a relatshionship b/w independant variables(ratings, distance, reviewcount , type of restaurant) and available  bikes ( want to find what lowers avialability = more users) . I did not have enough independent variables to conduct a meaningful regression analysis , so I converted the restaurants to boolean 0 or 1 values ie.is_bar (if it is then 1 if not then 0) to see if the type of venue had anything to do with available bikes. onve I added those, one by one ie. forward stepwise regression  the R Squared value rose slightly ( but still not enough)
7)interpret regression results. All P-values were above the defined significance level of %5 excpet for is_Mexican ( meaning that there is avery low chance that a restaurant which is Mexican would have a relationship with avialble bikes if we assume the null hypothesis is true). THe R- Squared and Adjusted R Squared were both too low - meaning that the independent variables explain only ~ %4.4 of variance in available bikes . 

8)idea for classification model


## Results

quality and quantity were not sufficient to train a robust regression model . APi request limits diminshed the completeness of the datasets. I learnt a lot from this hands-on experience of working with APIs , JSON files , dataframes , SQL in Python , data visualiztions with matplotlib and seaborn and performing regression tests. Although it was challenging , after my presentation I felt accomplished which made the hard work worthwhile .

## Challenges 

the API limit and not knowing if parsing through the response counts as a requests!
shortage of time - if I had more time the API limit would not be a problem ( it resets every day ) and I would contact more regression tests to find out the most information possible about my data


## Future Goals
Parse through the data and extract greater detail in order to perform deeper more robust analysis – get more than one restaurant per station so regression model can be well trained

diagnostic tests to test for linearity , normality of each feature and residuals before performing regression test. After  I would test for homoscedasticity to see if variance of residuals is constant

Request APIs /get data for other characteristics around each bike station like demographics (ie,avg. age , income, occupation in order to discover dif. relationships these factors could have
 would also perform Shapiro WIlks test to test for normality of different features .

THANk YOU ! 