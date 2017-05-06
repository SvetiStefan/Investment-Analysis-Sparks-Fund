# Sparks Fund Investment Analysis
### Objectives
Spark Funds wants to make investments in a few companies. The CEO of Spark Funds wants to understand the global trends in investments so that she can take the investment decisions effectively.

#### Spark Funds have two minor constraints for investments:
* They want to invest between 5 to 15 million USD per round of investment.
* They want to invest only in English-speaking countries because of the ease of communication with the companies they’d invest in.

Spark Funds wants to invest where **most other investors** are investing. This pattern is often observed among early stage start-up investors.

The data is from real investment db from crunchbase.com, so the insights we get are incredibly useful.

We have 3 data files for the analysis
* companies.txt: A text file with basic data of companies.
* rounds2.csv: A csv file with data about investments
* mapping_file.csv: This file maps the numerous sector names (like 3D printing, aerospace, agriculture etc.) to 8 main sector names. The purpose of having 8 main sectors is to simplify the analysis into 8 sector buckets, rather than trying to analyse hundreds of them.

(The code for this is present in the file analysis_r_code)
#### The business objectives and goals of data analysis are:
**Business objective:**  The objective is to identify the best sectors, countries and a suitable investment type for making investments. The overall strategy is to invest where others are investing, implying that the best sectors and countries are the ones where most investments are happening.
#### Goals of data analysis: our goals are divided into 3 main sub-goals:
**Investment type analysis:** Understanding investments in venture, seed/angel, private equity categories etc. so Spark Funds can decide which type is best suited for their strategy.
**Country analysis:**  Understanding which countries have had the most investments in the past. These will be Spark Funds’ favourites as well.
**Sector analysis:** Understanding the distribution of investments across the 8 main sectors (note that we are interested in the 8 main sectors provided in the mapping file. The 2 files, companies and rounds2, have numerous sub-sector names; hence we will need to map each sub-sector to its main sector).

##### Data Cleaning
* Load the two files companies.txt and rounds2.csv into two data frames and name them companies and rounds2 respectively.
* Replace all the NA values from the raised_amount_usd column of the master frame

The funding types like seed, venture, angel etc. depend upon the type of the company (start-up, corporate etc.), its stage (early stage start-up, funded start-up etc.), the amount of funding (a few million USD to a billion USD) etc. For example, seed, angel and venture are three common stages of start-up funding.
Seed / angel funding refer to early stage start-ups whereas venture funding occurs after seed / angel stage(s) and involves a relatively higher amount of investment.
Private equity type investments are associated with much larger companies and involve much higher investments than venture type. Start-ups which have grown in scale may also receive private equity funding. This means if a company has reached venture stage, it would have already passed through angel / seed stage(s).

**Funding Type Analysis** :-   Considering the constraints of Spark Funds, we will find one funding type most suitable for them.

**Country Type Analysis** :- Spark Funds wants to invest in countries having the highest amount of funding for the chosen investment type. This is a part of their broader strategy to invest where most investments are occurring.
 
Spark Funds wants to see the top 9 countries which have received the highest total funding (across ALL sectors for the chosen investment type).
For the chosen investment type, we will make a data frame named top9 with top9 countries (based on the total investment amount each country has received).

**Sector Analysis** :-    When we say sector analysis, we refer to one of the 8 main sectors (named main_sector) listed in the mapping file (note that ‘Other’ is one of the 8 main sectors). This is to simplify the analysis by grouping the numerous category lists (named ‘category_list’) in the mapping file. For example, in the mapping file, category_lists like ‘3D’, ‘3D Printing’, ‘3D Technology’ etc. are mapped to the main sector ‘Manufacturing’.

Also, for some companies, category list is a list of multiple sub-sectors separated by a pipe (vertical bar, |). For example, one of the companies’ category_list is Application Platforms|Real Time|Social Network Media.
 
The business rule tells you that the first string before the vertical bar will be considered the primary sector. In the example above, ‘Application Platforms’ will be considered the primary sector.

We extract the primary sector of each category list from the category_list column.
Use mapping file "mapping.csv" to map each primary sector to one of the 8 main sectors. (Note that ‘Others’ is also considered one of the main sector)

Now you have a data frame with each company’s main sector (main_sector) mapped to it. When we say sector analysis, we refer to one of the 8 main sectors.
Also, you know the top 3 English speaking countries and the most suitable funding type for Spark Funds. Let’s call the three countries Country 1, Country 2 and Country 3 and the funding type FT.
Also, the range of funding preferred by Spark Funds is 5 to 15 million USD.
 
Now, the aim is to find out the most heavily invested main sectors in each of the three countries (for funding type FT and range of investment between 5-15 M USD).
 
Create three separate data frames D1, D2 and D3 for each of the 3 countries containing the observations of funding type FT  falling between 5 to 15 million USD range. The three data frames should contain:
* All the columns of the master_frame along with the primary sector and the main sector
* The total number (or count) of investments for each main sector in a separate column
* The total amount invested in each main sector in a separate column
* Using the three data frames, we can calculate the total number and amount of investments in each main sector.

##### Analysis_presentation.pdf is also included in the repository which explains the results of the analysis

 







