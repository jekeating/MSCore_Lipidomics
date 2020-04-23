# MSCore_Lipidomics

This is designed to take integrated peak areas of isotopically labeled internal standards (calculated by QuanBrowser) and use them to normalize the integrated peak areas of endogenous lipid species (calculated by LipidSearch).

#Instructions:
Download the repository as a zip file, extract and move to desktop

1. Mass accuracy check - load your data in QualBrowser and apply the MassAccuracyCheck_Equisplash.lyt layout  
  a. If the MS2 blocks show no data change the filter to the closest mass (same polarity), sometimes the DDA mass is not exactly the same as the one in the layout  
  b. Fill out the MassAccuracyCheck.xlsx document, make processing decisions based on the mass error in each polarity at the start and end 
      of the queue (either reinject or post-run correct)
      
2. Get internal standard peak areas in QuanBrowser using the Default_20min_100mmC18.pmd processing method  
  a. Review peak integration, manually reintegrate only if absolutely necessary  
  b. Export to short excel report (example is given as integrationresults_Short.xlsx (IPAvsMTBE data) and
      PLC_quanbrowserresults_Short.xlsx (PLC knockout data
 
3. Generate LipidSearch export document as Lipid Ion - Validated Ions (example given as IPA_vs_MTBE_Lsearch.txt and PLC_alignment.txt)
  a. Follow video instructions under MSCore Microsoft Teams for help using LipidSearch
  
4. Open MainWorkupScript.Rmd in Rstudio and work your way down the individual code chunks (using green play button)  
  a. Locations for user input are all in the first code chunk, briefly they are:  
    i. Quanbrowser file names    
    ii. Lipidsearch file name  
    iii. Mass accuracy check file name     
    iv. File path for the files above  
  b. The only other user input (if not visualizing data in R) is the internal standards selection spreadsheet  
    i. A code chunk will export IS_choices.csv to the directory originally chosen  
    ii. Fill this out and resave as Completed_IS_choices.csv (an example of the completed version is in the example data folder)  
    iii. All possible internal standards are listed in the second column, can also input 'dummy' to keep a lipid class and divide all 
        areas by 1 (no normalization)  
    iv. If you dont have an internal standard for a class and don't want to use the dummy variable you can just delete it from first 
        column, lipids from that class will not be included in final outputs  
  c.The script will output a .csv that can be visualized in Metaboanalyst.ca or in processing software of choice 
    (example given as PLC_metaboanalyst_input.csv)
    
    
 
