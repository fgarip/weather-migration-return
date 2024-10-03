# weather-migration-return
PNAS article "Weather deviations linked to undocumented migration and return between Mexico and the United States"

1.	To replicate the analysis, download the following STATA do-files. The code was written on STATA/MP 18.

project_master.do
data_clean.do
data_analysis.do

2.	The analysis uses the MMP data from 170 communities. This is reflected in suffix (170 or 2019) after each original data file. If using a later version of the data, make sure to change the suffix (to 170 or 2019) to use the code as is. (Alternatively, update
the globals "mmp_version" and "mmp_year" to your version/year of the data in project_master.do).

3.	The MMP data set will soon move to Brown University. (Date currently unkown.) Please e-mail the new co-director of the MMP Project, David Lindstrom (david_lindstrom@brown.edu) for the new data link.

4.	Download the MMP data. The data are currently split across two archives.

a.	Obtain the first set of files from https://mmp.opr.princeton.edu/databases/supplementaldata-en.aspx

commun170.dta
nathist2019.dta
natlyear2019.dta
prevratio170.dta

b.	Obtain the second set of files from https://oprdata.princeton.edu/Archive/MMP/. You will need to register as a user of the data archive. 

house170.dta
life170.dta
mig170.dta
migother170.dta
pers170.dta
spouse170.dta


5.	Obtain the following supplementary files created by the authors from Filiz Garip (fgarip@princeton.edu).
		
commun_dist.dta 		(distance of each community to the US border)
commun_state.dta		(state codes for each community)
const10.dta			(scalar for conversion to constant 2010 US$)
mmp_data_*.tsv 	(daily temperature and precipitation data for each community for each year *)

These data and code files are sufficient to replicate the analysis in the paper. 

If you are interested in obtaining the source code for generating the weather data, please see the information below. 



**Steps involved in creating the weather data**

To download weather data for the MMP communities, first obtain permission from the MMP team to access community-level identifiers by emailing the co-director of the MMP Project, David Lindstrom at Brown University (david_lindstrom@brown.edu). Then, obtain the following files from the corresponding author, Filiz Garip (fgarip@princeton.edu).

obtain_weather_data.Rproj	(R project file)
daymet_collect.R		      (function to download Daymet data)
create_mmp_shapefile.R	  (saves shapefiles for MMP communities)
get_daymet_for_mmp.R.     (gets Daymet data for MMP communities)

Save these documents in a folder. Follow these steps:

1.	Create a CSV document with community IDs and geocodes titled “mmp_geocodes.csv”. (If you have obtained permission for restricted-data use, you can also obtain this document from the corresponding author, Filiz Garip.)

2.	Create a subfolder named “shapefiles.” Within that subfolder, create a folder titled “mx_mun”.

3.	Mexico shapefiles come from Mexico’s INEGI (National Institute of Statistics and Geography)  website. Our project uses the "Marco Geoestaditico, febrero 2018", which can be downloaded at this link. A more recent version (diciembre 2023) is available here. 

4.	Download and unzip all folders. There is a separate folder for each state. Put all folders in the subfolder titled “mx_mun”.

5.	Open R-project file obtain_weather_data.Rproj in R Studio. (Please use the most recent version of R and R Studio.) 

6.	Open and run create_mmp_shapefile.R. This code will create a sub-folder called “mmp_loc” in the “shapefiles” folder.

7.	Open and run get_daymet_for_mmp.R. This code will call the function daymet_collect.R to download the weather data from DAYMET for the area defined by MMP community shapefiles. This code takes a very long time to run.  


