# Analysis of Reported Crime in New York City

## Abstract

This research project analyzes crime report data from the city of New York. The data being examined is from two years, 2006 and 2017. I do an analysis on both the number and types of crimes in the city. I compare these numbers between the two years and do a thorough analysis. 

The complete and thorough analysis is available in the file [Data-512-Final-Project.ipynb](./Data-512-Final-Project.ipynb). This file contains both the code as well as the report for the analysis.

This project was developed for Data 512 (Human Centered Data Science), University of Washington. This is my final project for the course. 

## Data

I used the **NYPD Complaint Data Historic** dataset. According to the webpage, this dataset "includes all valid felony, misdemeanor, and violation crimes reported to the New York City Police Department (NYPD) from 2006 to the end of last year (2017)." The data is available as a part of the NYC OpenData program. This data is publicly available and there are no restrictions regarding the usage of the data.

The about page available [here](http://www.nyc.gov/html/data/about.html) clearly states that anyone can use the data available on the NYC Open Data site. I reproduce the relevant parts of the about page below.

> NYC Open Data makes the wealth of public data generated by various New York City agencies and other City organizations available for public use. As part of an initiative to improve the accessibility, transparency, and accountability of City government, this catalog offers access to a repository of government-produced, machine-readable data sets. Anyone can use these data sets to participate in and improve government by conducting research and analysis or creating applications, thereby gaining a better understanding of the services provided by City agencies and improving the lives of citizens and the way in which government serves them.

The NYC Open Data Terms of Use is reproduced below, and it is also available [here](https://opendata.cityofnewyork.us/overview/#termsofuse).

> By accessing datasets and feeds available through NYC Open Data, the user agrees to all of the [Terms of Use](http://www1.nyc.gov/home/terms-of-use.page) of NYC.gov as well as the [Privacy Policy](http://www1.nyc.gov/home/privacy-policy.page) for NYC.gov. The user also agrees to any additional terms of use defined by the agencies, bureaus, and offices providing data. Public data sets made available on NYC Open Data are provided for informational purposes. The City does not warranty the completeness, accuracy, content, or fitness for any particular purpose or use of any public data set made available on NYC Open Data, nor are any such warranties to be implied or inferred with respect to the public data sets furnished therein.
>
> The City is not liable for any deficiencies in the completeness, accuracy, content, or fitness for any particular purpose or use of any public data set, or application utilizing such data set, provided by any third party.
>
> Submitting City Agencies are the authoritative source of data available on NYC Open Data. These entities are responsible for data quality and retain version control of data sets and feeds accessed on the Site. Data may be updated, corrected, or refreshed at any time.

### NYPD Complaint Data Historic

This dataset contains all valid crimes that were reported to the NYPD from 2006 till the end of 2017. These crimes include felonies, misdemeanors and other violent crimes. The dataset is very comprehensive, containing 6,036,095 rows of reported crime. You can download the data as a dump containing all the data, or programmatically access it using the Socrata Open Data (SODA) API. There are 35 columns in the dataset. To make things easier for you, a data dictionary (available [here](https://data.cityofnewyork.us/api/views/qgea-i56i/files/ee823139-888e-4ad0-badf-e18e2674a9cb?download=true&filename=NYPD_Complaint_Historic_DataDictionary.xlsx)) provides a comprehensive description of the different columns and what they contain. Only the subsetted data that is required for this research is included in this repository. 

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

I use a bucketed form of data that consolidates the 62 different kinds of crimes into 10 different buckets. This has been cached in the repository, and by default, the notebook uses the cached version. You can also process the data yourself and use that, however, it is a time consuming process that takes ~5 hours. There is an option in the notebook to disable the cache and create your own data.

## Reproducibility

This research is fully reproducible. That means you can conduct this research and get the exact results that are shown in the notebook. To begin with, you need to download the repository by executing the following command: `git clone https://github.com/tejasmhos/data-512-final-project`. This will download the code and data required for the analysis. After doing this, All you need to do is start the Jupyter notebook and execute all the cells. 

No additional data has to be downloaded to reproduce this analysis as it is stored on the repository. Dependencies need to be installed, which are detailed in the tools section below.

## Tools

This analysis was conducted using Python 3.6 on a Macbook Pro early 2015 laptop. I used a number of different Python packages. The packages that were used were `pandas`, `matplotlib`, `seaborn`, `numpy` and `copy`. If you get an import error while conducting the research, it is quite simple to install the missing package. Just run `pip install package_name`. 

# References

[1] https://en.wikipedia.org/wiki/New_York_City%C2%A0

[2] https://data.cityofnewyork.us/Public-Safety/NYPD-Complaint-Data-Historic/qgea-i56i

[3] https://en.wikipedia.org/wiki/Boroughs_of_New_York_City

[4] https://www.nap.edu/catalog/23492/modernizing-crime-statistics-report-1-defining-and-classifying-crime

[5] https://www.city-journal.org/html/how-new-york-became-safe-full-story-13197.html

