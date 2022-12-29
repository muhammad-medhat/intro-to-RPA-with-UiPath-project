# Sorting Annual Reports 
    In this project, an automation has been developed for a process that sorts files in a given folder into sub-folders based on the date in the file name.
    This project involves navigating to a webpage and downloading a zip file to sort. You have to move the file to a particular folder depending upon the process requirement:

## Environment & Tools
    Below are the Project requirements and dependencies needed for building the project:

* Hardware and Software requirement of your Desktop or Laptop
* UiPath Studio uipath studio 2022.12.0 community edition
* Web Browser
* Access to the Internet
* Read-write permission in the machine where UiPath Studio is installed.




## Workflows
This type of automation is an **unattended automation** since it doesn't require any user interaction, were all interactions are handled by the following workflows.
* Main.xaml (main workflow)
* Set_environment_Path.xaml
* Start_and_download.xaml
* Move_and_unzip.xaml
* Sorting_Files_Proc.xaml

### Main.xaml
    That is the main workflow that manages passing arguments between the other workflows in this unattended automation.

### Set_environment_Path.xaml
    Setting the initial values to be used in our automation.

* **Pre-conditions:** starting the application
* **Post-conditions:** returns the downloaded file name

#### Arguments
* out_currentPath *Type String*
* out_dPath *Type String*
* out_username *Type String*

### Start_and_download.xaml
    Starting the Google Chrome browser to download the zip file of our repo from github.

* **Pre-conditions:** providing the path to download
* **Post-conditions:** returns the downloaded file name

#### Arguments
* in_dPath *Type String*
* out_fileName *Type String*

### Move_and_unzip.xaml
    Moving the downloaded zip file to the project path then unzip the file.

* **Pre-conditions:** the the ile is downloaded in the downloads folder. 
* **Post-conditions:** will move and extract the downloaded file in the project's folder.  

#### Arguments
* out_workingFilesFolder *Type: String*
* out_dataFolder *Type:DirectoryInfo*
* in_fileName *Type: String*
* in_currentPath *Type: String*
* in_dPath *Type: String*

### Sorting_Files_Proc.xaml
    For each file in the folder that follows this naming convention “CustomerName_Report_DDMMYYYY.xlsx/.pdf”, create a folder named “YYYY”(Date format) depending on the last four characters of the file name, which denotes the year in the “YYYY”(date format). For example, if the file name is “Heba_Report_13072019.pdf” then create a folder with the name “2019” and move the file into this folder. If any of the files don't follow the naming convention, then create a new folder with today’s date (format MMDDYYYY) and move them there.

* **Pre-conditions:** the downloaded file is extracted on the project's folder. 
* **Post-conditions:** all the reports are moved to a folder denotes the year of that file. 

#### Arguments
* in_fileName *Type: String* 
    * name of the file to extract
    * *the same name will be used for the folder containing the extracted files*
* in_dataFolder *Type: DirectoryInfo* 
    * is the folder of the extracted files
* in_workingFilesFolder *Type: String* 
    * name of the extracted files folder
