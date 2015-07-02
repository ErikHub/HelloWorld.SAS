# HelloWorld.SAS

## SAS Programming 1: Essentials  
Notes used in learning SAS Programming Language  

`Every SAS Statement ends in a semicolon;`  

`* Comments can start with an asterisk and end with a semicolon; or`  
`/* Comments can be commented with a forwardslash and semicolon */ but the first one is better due to some operating systems ending jobs with /*`  
  
`%let path=FILEPATH; `  
`libname orion "&path";`  
You have defined the orion library and SAS knows where you are storing your practice files.  
  
  For SAS University Edition on AWS Marketplace:  
When you stop an instance of SAS University Edition (or if the instance times out), the practice data persists. You must open and submit the setup.sas program to access your practice data in the orion library.  
When you terminate an instance of SAS University Edition, the practice data is deleted along with the instance. You must perform Task 1 and Task 2 when you create a new instance.  


### SAS is for Accessing, Managing, Analyzing, and Presenting Data.  
_Access_: SAS can access files from Excel, Oracle, raw data, or other types of files.  
	Raw Data Files: Files that have not been processed by any other program. File contains non-software-specific data. Unformatted text.  
	SAS Datasets: Proprietary data format created and read by SAS core.  
	SAS Program Files:  Contains SAS programming code on how to process certain data.  
_Manage_: You can subset data, create variables, validate or clean data, or combine data to ready it for analysis.  
_Analysis_: You can perform frequency counts, or calculate averages easily. SAS is the gold standard when it comes to Statistical Analysis, and you can perform regression or forecasting.  
_Present_: You can create list reports, summary reports, or graphic reports to share your findings meaningfully.  
  
### SAS Programming Process  
- Define the business need.  
- Write a SAS program.  
- Run the program.  
- View the results.  
- Debugging takes you back to writing the SAS program.  