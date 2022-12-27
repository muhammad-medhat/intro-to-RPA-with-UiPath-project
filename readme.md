# Sorting Annual Reports 
In this project, an automation has been developed for a process that sorts files in a given folder into subfolders based on the date in the file name.

This project involves navigating to a webpage and downloading a zip file to sort. You have to move the file to a particular folder depending upon the process requirement:

For each file in the folder that follows this naming convention “CustomerName_Report_DDMMYYYY.xlsx/.pdf”, create a folder named “YYYY”(Date format) depending on the last four characters of the file name, which denotes the year in the “YYYY”(date format). For example, if the file name is “Heba_Report_13072019.pdf” then create a folder with the name “2019” and move the file into this folder.
If any of the files don't follow the naming convention, then create a new folder with today’s date (format MMDDYYYY) and move them there.
## Workflows
* Main.xaml (main workflow)
* Set_environment_Path.xaml
* Start_and_download.xaml
* Move_and_unzip.xaml
* Sorting_Files_Proc.xaml

### Main.xaml
it is the main workflow that manages passing arguments between the other workflows.

### Set_environment_Path.xaml
Setting the initial values to be used in our automation.

### Start_and_download.xaml
Starting the Google Chrome browser to download the zip file of our repo from github

### Move_and_unzip.xaml
Moving the file to the project path then unzip the file.

### Sorting_Files_Proc.xaml
Sorting reports found in this directory according to the year of issue.
