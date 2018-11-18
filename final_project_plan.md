# Final Project Plan - Analysis of Crime in New York City

Tejas Hosangadi

Data 512 (Human Centered Data Science)

Fall 2018

## Introduction

New York City (NYC) is the largest city in the United States, and one of the most influential cities in the world. It has a population of 8,175,133 as of 2010. It's a very diverse city with people from all around the world. 

According to Wikipedia, crime has been steadily falling in NYC since the early 1990s, and it is considered to be one of the safest city in the world. The city of New York is divided into  5 boroughs (administrative divisions). It would be interesting to analyse the types of crime and number of crimes committed by borough, and do an analysis on how social and economic factors effect the type and number of crimes committed in specific boroughs. 

I plan to analyse the New York City Complaint Data, which, according to the webpage, contains "all valid felony, misdemeanor, and violation crimes". I will not be using the entire dataset, as it spans from 2006 to 2017. I will be using data from 2006 and 2017, so two years worth of data. 

My plan is to do an analysis on the number of reported crimes in 2006 and 2017. My goal is to identify trends in the crime rate and discover insight in the number and types of crimes committed in the city as well as the boroughs that the city is divided into.

## Data

I will be using the **NYPD Complaint Data Historic** dataset. According to the webpage, this dataset "includes all valid felony, misdemeanor, and violation crimes reported to the New York City Police Department (NYPD) from 2006 to the end of last year (2017)." The data is available as a part of the NYC OpenData program. This  data is publicly available and there are no restrictions regarding the usage of the data. 

For clarity, I have reproduced the Open Data Terms of Use below, and it is also available [here](https://opendata.cityofnewyork.us/overview/#termsofuse).

> By accessing datasets and feeds available through NYC Open Data, the user agrees to all of the [Terms of Use](http://www1.nyc.gov/home/terms-of-use.page) of NYC.gov as well as the [Privacy Policy](http://www1.nyc.gov/home/privacy-policy.page)  for NYC.gov. The user also agrees to any additional terms of use  defined by the agencies, bureaus, and offices providing data. Public  data sets made available on NYC Open Data are provided for informational  purposes. The City does not warranty the completeness, accuracy,  content, or fitness for any particular purpose or use of any public data  set made available on NYC Open Data, nor are any such warranties to be  implied or inferred with respect to the public data sets furnished  therein.
>
> The City is not liable for any deficiencies in the completeness,  accuracy, content, or fitness for any particular purpose or use of any  public data set, or application utilizing such data set, provided by any  third party.
>
> Submitting City Agencies are the authoritative source of data  available on NYC Open Data. These entities are responsible for data  quality and retain version control of data sets and feeds accessed on  the Site. Data may be updated, corrected, or refreshed at any time.

### NYPD Complaint Data Historic

This dataset contains all valid crimes that were reported to the NYPD from 2006 till the end of 2017. These crimes include felonies, misdemeanors and other violent crimes. The dataset is very comprehensive, containing 6,036,095 rows of reported crime. There are 35 columns in the dataset. To make things easy for the user of the dataset, a data dictionary (available [here](https://data.cityofnewyork.us/api/views/qgea-i56i/files/ee823139-888e-4ad0-badf-e18e2674a9cb?download=true&filename=NYPD_Complaint_Historic_DataDictionary.xlsx)) provides a comprehensive description of the different columns and what they contain. My final repository will also contain this dictionary to make things easier for the end user. A description of the columns is shown below:

| Name              | Data Type | Description                                                 |
| ----------------- | --------- | ----------------------------------------------------------- |
| CMPLNT_NUM        | Number    | Random ID that's unique.                                    |
| CMPLNT_FR_DT      | Datetime  | The date when the crime was reported.                       |
| CMPLNT_FR_TM      | Datetime  | The time when the crime was reported.                       |
| CMPLNT_TO_DT      | Datetime  | The end date for the reported crime.                        |
| CMPLNT_TO_TM      | Datetime  | The end time for the reported crime.                        |
| ADDR_PCT_CD       | Number    | The precinct where the crime occurred.                      |
| RPT_DT            | Datetime  | Date when it was reported to the police.                    |
| KY_CD             | Number    | Three digit offense code.                                   |
| OFNS_DESC         | Text      | Description of the offense.                                 |
| PD_CD             | Number    | Internal classification code.                               |
| PD_DESC           | Text      | Description of the internal classification code.            |
| CRM_ATPT_CPTD_CD  | Text      | Indicates is crime was successful or a failed attempt.      |
| LAW_CAT_CD        | Text      | Level of the offense: felony, misdemeanor or violation.     |
| BORO_NM           | Text      | Name of the Borough.                                        |
| LOC_OF_OCCUR_DESC | Text      | Description of where the crime occurred.                    |
| PREM_TYP_DESC     | Text      | Specific description of premises where crime occurred.      |
| JURIS_DESC        | Text      | Description of JURISDICTION_CODE                            |
| JURISDICTION_CODE | Number    | The jurisdiction responisble for the incident.              |
| PARKS_NM          | Text      | Name of the park, playground or greenspace (if applicable). |
| HADEVELOPT        | Text      | Name of NYCHA housing development (if applicable).          |
| HOUSING_PSA       | Text      | Development level code.                                     |
| X_COORD_CD        | Number    | X-coordinate for NYS Plane Coordinate system.               |
| Y_COORD_CD        | Number    | Y-coordinate for NYS Plane Coordinate system.               |
| SUSP_AGE_GROUP    | Text      | The suspects age group.                                     |
| SUSP_RACE         | Text      | The suspects race.                                          |
| SUSP_SEX          | Text      | The suspects sex.                                           |
| TRANSIT_DISTRICT  | Number    | Transit district where crime occurred.                      |
| Latitude          | Number    | The latititude at which crime occurred.                     |
| Longitude         | Number    | The longitude at which crime occurred.                      |
| Lat_Lon           | Location  | Lat-Long location.                                          |
| PATROL_BORO       | Text      | The name of the patrol borough where incident occurred.     |
| STATION_NAME      | Text      | The name of the transit station.                            |
| VIC_AGE_GROUP     | Text      | The age group of the victim.                                |
| VIC_RACE          | Text      | The race of the victim.                                     |
| VIC_SEX           | Text      | The sex of the victim                                       |

The data will need to be processed before it can be used for my analysis. The first and most obvious step is to filter the data so that it contains events from 2006 and 2017 only, as my analysis deals with data in this date range. I will filter the data and place it as a CSV in the repository to ensure reproducibility of my results.

I also anticipate that a number of columns will not really serve me any purposes. These columns will need to be removed after further analysis of the data that I conduct during my research. I 