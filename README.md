# data_science

The main file is called  Final_report-Copy1.ipynb it contains all the code that was written to carry out this analysis, figures and plots. 

Extra libraries used

uszipcode https://pypi.org/project/uszipcode/ library that uses crawler running every week to get data from various data sources. They provide quite a lot of information about the zip code, like the state, timezone, radiusof the postcode, stats and demographics, housing info, employment and education, etc. The example can be seen in notebook. (uncomment line. ) pip install uszipcode



Plotly is a python library that creates interactive, publication-quality graphs (as they claim). The library is full of various presets and I used their script to draw the US map as on CDC website. Can be installed with pip install plotly
 


Re #regular expressions for python the module was used to work with strings, 
https://docs.python.org/3/library/re.html 
https://docs.python.org/3/howto/regex.html

I used regex to work with txt files for fmri analysis for my thesis, and wanted something familiar to work with strings for python. 





cdc_death_mappers - function (to the greater extent modified by me, that maps conditions to the numbers in CDC dataset) saved separately to save some space in notebook. The function is supplied in the folder


For this code to run it requires set of csv files downloaded from CDC and dolt database from Dolt websites. 

Dolt hospital transparency prices v2. 

The data-set can be found here 
https://www.dolthub.com/repositories/dolthub/hospital-price-transparency-v2

Please note, that the team continues working on it, and I noticed that it was updated 3 hours ago (I am a bit too scared to risk downloading it now and correcting all the numbers) in case you will need the version of the data I was working with, 

https://drive.google.com/drive/folders/1uNNR3WKtC0E0xXjLJpkzWsizCrNpDNaM?usp=sharing

Here is the link to download the version i was working on. To use it download and add unzipped folder to the main notebook directory

The instructions how to install dolt-hub for your machine are here https://docs.dolthub.com/getting-started/installation 

After the installation is complete, you need to run the following line in your terminal 

dolt clone dolthub/hospital-price-transparency-v2 

and copy folder with the saved files to the notebook folder in case the name is different than in the notebook this should be amended to match
 
This is the about dataset page  (with the detailed description of the current dataset tables )

https://www.dolthub.com/repositories/dolthub/hospital-price-transparency-v2/doc/master 


Then you would need Doltpy Python API for code to run which can be found here 

https://docs.dolthub.com/interfaces/python 
And also 
https://github.com/dolthub/doltpy

When the dolt will be working next step is to get the first part of the CDC wonder dataset that I have abandoned 

It can be downloaded here 
https://www.cdc.gov/nchs/data_access/vitalstatsonline.htm#Mortality_Multiple 
Middle section, 2019. 
documentation_for_CDC_mortality folder also contains saved pdf file which provides 

the key locations for the data

There is section in the appendix that parses the data into correct CSV format file that is supplied VS19MORT.zip (it should be named VS19MORT.csv )

To work with it please unzip it and put into the directory with the notebook. 

For the second part of the mortality analysis you wold need  flowing files : 

 hospitals_per_ahd.com.csv
This is the file that I created myself. One part of it is copied from the code (how many hospitals were claimed to be present in the data-set) the other column is taken from the 
https://www.ahd.com/ website. Go to the https://www.ahd.com/search.php 
And select one state, eg AK (Alaska), click submit on the top right 
The result will provide you with the total of hospitals per that state, eg 28 for Alaska. 
Click on search again and repeat with states of interest. The results are stored in hospitals_per_ahd.com.csv table 

ZIP-COUNTY-FIPS_2018-03.csv is the list of FIPS codes for the US states and counties and can be downloaded from here : 
https://data.world/niccolley/us-zipcode-to-county-state/activity  

Flowing files are queries from CDC wonder website, and these were modified by me as pandas had issues with headings unless modified! So I recommend to youse these files with given demographics

The following files were obtained using CDC wonder system

https://wonder.cdc.gov/mcd-icd10-expanded.html 

The settings for each query are as follows 

infants_death_birth_complication.csv

Dataset: Multiple Cause of Death, 2018-2019, Single Race
Query Parameters:
Ten-Year Age Groups: < 1 year
UCD - ICD-10 130 Cause List (Infants): Newborn affected by maternal factors and by complications of pregnancy, labor and
delivery (P00-P04)
Group By: Single Race 6
Show Totals: True
Show Zero Values: True
Show Suppressed: True
Calculate Rates Per: 100,000
Rate Options: Default intercensal populations for years 2001-2009 (except Infant Age Groups)


FLORIDA_I21_I22_I24_totals.csv

Dataset: Multiple Cause of Death, 2018-2019, Single Race
Query Parameters:
Title: FLORIDA_counties_I_21_I22_I24_totals
States: Florida (12)
UCD - ICD-10 113 Cause List: Acute myocardial infarction (I21-I22); Other acute ischemic heart diseases (I24)
Year/Month: 2019
Group By: County
Show Totals: True
Show Zero Values: True
Show Suppressed: True
Calculate Rates Per: 100,000
Rate Options: Default intercensal populations for years 2001-2009 (except Infant Age Groups)


MCD_michigan_total_per_county.csv

Dataset: Multiple Cause of Death, 2018-2019, Single Race
Query Parameters:
Title: MCD_michigan_total_per_county
States: Michigan (26)
UCD - ICD-10 113 Cause List: Acute myocardial infarction (I21-I22); Other acute ischemic heart diseases (I24)
Year/Month: 2019
Group By: County
Show Totals: True
Show Zero Values: True
Show Suppressed: True
Calculate Rates Per: 100,000
Rate Options: Default intercensal populations for years 2001-2009 (except Infant Age Groups)



MCD_south_dakota_total_per_county.csv

Dataset: Multiple Cause of Death, 2018-2019, Single Race
Query Parameters:
Title: MCD_south_dakota_total_per_county
States: South Dakota (46)
UCD - ICD-10 113 Cause List: Acute myocardial infarction (I21-I22); Other acute ischemic heart diseases (I24)
Year/Month: 2019
Group By: County
Show Totals: True
Show Zero Values: True
Show Suppressed: True
Calculate Rates Per: 100,000
Rate Options: Default intercensal populations for years 2001-2009 (except Infant Age Groups)


MCD_south_dakota_total_per_county_race.csv
Dataset: Multiple Cause of Death, 2018-2019, Single Race
Query Parameters:
Title: MCD_south_dakota_total_per_county_race
States: South Dakota (46)
UCD - ICD-10 113 Cause List: Acute myocardial infarction (I21-I22); Other acute ischemic heart diseases (I24)
Year/Month: 2019
Group By: County; Single Race 6
Show Totals: True
Show Zero Values: True
Show Suppressed: True
Calculate Rates Per: 100,000
Rate Options: Default intercensal populations for years 2001-2009 (except Infant Age Groups)



Multiple Cause of Death, michigan2019_by_county, Single Race.csv

Dataset: Multiple Cause of Death, 2018-2019, Single Race
Query Parameters:
Title: Multiple Cause of Death, michigan2019_by_county, Single Race
States: Michigan (26)
UCD - ICD-10 113 Cause List: Acute myocardial infarction (I21-I22); Other acute ischemic heart diseases (I24)
Year/Month: 2019
Group By: County; Single Race 6
Show Totals: True
Show Zero Values: True
Show Suppressed: True
Calculate Rates Per: 100,000
Rate Options: Default intercensal populations for years 2001-2009 (except Infant Age Groups)

stroke_10y_groups_ages_races.csv

Dataset: Multiple Cause of Death, 2018-2019, Single Race
Query Parameters:
Title: stroke_10y_groups_ages_races
Gender: Male
UCD - ICD-10 113 Cause List: #Cerebrovascular diseases (I60-I69)
Year/Month: 2019
Group By: Single Race 6; Ten-Year Age Groups
Show Totals: True
Show Zero Values: True
Show Suppressed: True
Calculate Rates Per: 100,000
Rate Options: Default intercensal populations for years 2001-2009 (except Infant Age Groups)



stroke_all_ages_races.csv

Dataset: Multiple Cause of Death, 2018-2019, Single Race
Query Parameters:
Title: stroke_all_ages_races
Gender: Male
UCD - ICD-10 113 Cause List: #Cerebrovascular diseases (I60-I69)
Year/Month: 2019
Group By: Single Race 6
Show Totals: True
Show Zero Values: True
Show Suppressed: True
Calculate Rates Per: 100,000
Rate Options: Default intercensal populations for years 2001-2009 (except Infant Age Groups)



total_deaths_races_michigan.csv

Dataset: Multiple Cause of Death, 2018-2019, Single Race
Query Parameters:
States: Michigan (26)
UCD - ICD-10 113 Cause List: Acute myocardial infarction (I21-I22); Other acute ischemic heart diseases (I24)
Year/Month: 2019
Group By: Single Race 6
Show Totals: Disabled
Show Zero Values: False
Show Suppressed: False
Calculate Rates Per: 100,000
Rate Options: Default intercensal populations for years 2001-2009 (except Infant Age Groups)


Michigan_I21_I23_I24_totals.csv

Dataset: Multiple Cause of Death, 2018-2019, Single Race
Query Parameters:
Title: Michigan_I21_I23_I24_totals
States: Michigan (26)
UCD - ICD-10 113 Cause List: Acute myocardial infarction (I21-I22); Other acute ischemic heart diseases (I24)
Year/Month: 2019
Group By: County
Show Totals: True
Show Zero Values: True
Show Suppressed: True
Calculate Rates Per: 100,000
Rate Options: Default intercensal populations for years 2001-2009 (except Infant Age Groups)

File headers are not read properly by Jupyter, so each file was modified before and header files were rewritten to ones that can be found in original supplied CSV files. 
Also, Note column was deleted, as well as state abbreviation from the county name. 

Where appropriate, suppressed death results (under 9) were replaced by zeros. 



us_heart_diseases.csv 

The file can be downloaded here 

https://www.cdc.gov/nchs/pressroom/sosmap/heart_disease_mortality/heart_disease.htm





us_states_names2.csv  was created manually using and fips file

https://www.nrcs.usda.gov/wps/portal/nrcs/detail/?cid=nrcs143_013696 
 

 








Installed versions of software I was working with 
INSTALLED VERSIONS
------------------
commit           : 2cb96529396d93b46abab7bbc73a208e708c642e
python           : 3.8.5.final.0
python-bits      : 64
OS               : Linux
OS-release       : 5.4.0-73-generic
Version          : #82-Ubuntu SMP Wed Apr 14 17:39:42 UTC 2021
machine          : x86_64
processor        : x86_64
byteorder        : little
LC_ALL           : None
LANG             : en_GB.UTF-8
LOCALE           : en_GB.UTF-8

pandas           : 1.2.4
numpy            : 1.19.0
pytz             : 2020.1
dateutil         : 2.8.1
pip              : 20.0.2
setuptools       : 56.1.0
Cython           : None
pytest           : None
hypothesis       : None
sphinx           : None
blosc            : None
feather          : None
xlsxwriter       : None
lxml.etree       : None
html5lib         : None
pymysql          : None
psycopg2         : None
jinja2           : 2.11.3
IPython          : 7.23.1
pandas_datareader: None
bs4              : None
bottleneck       : None
fsspec           : None
fastparquet      : None
gcsfs            : None
matplotlib       : 3.4.1
numexpr          : None
odfpy            : None
openpyxl         : None
pandas_gbq       : None
pyarrow          : None
pyxlsb           : None
s3fs             : None
scipy            : 1.6.3
sqlalchemy       : 1.4.13
tables           : None
tabulate         : None
xarray           : None
xlrd             : None
xlwt             : None
numba            : None
