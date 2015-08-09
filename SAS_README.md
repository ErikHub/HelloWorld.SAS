# HelloWorld.SAS

## SAS Programming 1: Essentials  
Notes used in learning SAS Programming Language  

`Every SAS Statement ends in a semicolon;`  
  
`%let path=FILEPATH; `  
`libname orion "&path";`  
You have defined the orion library and SAS knows where you are storing your practice files.  
  
  For SAS University Edition on AWS Marketplace:  
When you stop an instance of SAS University Edition (or if the instance times out), the practice data persists. You must open and submit the setup.sas program to access your practice data in the orion library.  
When you terminate an instance of SAS University Edition, the practice data is deleted along with the instance. You must perform Task 1 and Task 2 when you create a new instance.  


### SAS is for Accessing, Managing, Analyzing, and Presenting Data.  
__Access__: SAS can access files from Excel, Oracle, raw data, or other types of files.  

- _Raw Data Files_: Files that have not been processed by any other program. File contains non-software-specific data, or unformatted text.  
- _SAS Datasets_: Proprietary data format created and read by SAS core.  
- _SAS Program Files_:  Contains SAS programming code on how to process certain data.  

__Manage__: You can subset data, create variables, validate or clean data, or combine data to ready it for analysis.  
**Analysis**: You can perform frequency counts, or calculate averages easily. SAS is the gold standard when it comes to Statistical Analysis, and you can perform regression or forecasting.  
**Present**: You can create list reports, summary reports, or graphic reports to share your findings meaningfully.  
  
### SAS Programming Process  
- Define the business need.  
- Write a SAS program.  
- Run the program.  
- View the results.  
- Debugging takes you back to writing the SAS program.  

### Working with SAS Programs  
   
__SAS Programming STEPS__  
Generally speaking, a SAS program is a sequence of steps you submit to SAS for execution.  
Each step in the program accomplishes a specific task.  
Only two types of "Steps" in SAS programs. __PROC__ and __DATA__ steps.  
  
_Data_ Steps  
- A DATA step typically reads data from an input source, processes it, and creates a SAS data set, which is data in a form that SAS understands. One of the primary purposes of a DATA step is to create a SAS data set.  
- You can also use a Data Step to create new variables (Columns in Data) that were not in original data.  
_PROC_ Steps  
- A PROC or Procedure step typically processes SAS data sets. Various Procedures can generate reports, graphs, export data to print, manage data, and sort data.  
  
Typically an example would be the use of a _Data_ step to create a SAS Data set from raw data and then process it into a report using a _PROC_ step.  

_Global statements_ are neither DATA or PROC. Like a title that sticks on all pages of the report.  

A SAS program is made up of a series of Steps, and those steps are comprised of a series of sequences.  
You can tell when sequences begin because you'll see either DATA or PROC to mark the start of the sequence.  
These are called STEP boundaries.  
  
SAS detects the end of a step when:  
- it sees a run; statement
- it sees a quit; statement
- or it sees another step begin (DATA or PROC)  
It's good practice to explicitly end a statement. Like closing HTML.  

Syntax Rules and Commenting  
SAS statements usually begin with an identifying keyword, and they always end with a semicolon.  
Keywords identify the type of statement and semicolons end the statement.  
Each statement has an identifying keyword and ends with a semicolon.  

Using conventional formatting (that is, structured, consistent spacing) makes a SAS program easy to read.  
SAS statements can begin and end anywhere though, so they can look cluttered.
https://support.sas.com/edu/OLTRN/ECPRG193/eclibjr/eg_autoformat.htm For info on Enterprise edition auto-formatting.

Comments are for documentation or to explain the program, or for commenting out code.  
- Document Purpose  
- Non-executing Text  
- explain program  
You can comment out error-free code to test steps for bugs, or to test sections of the software in stages.  

Two ways to comment:SA
1. BLOCK COMMENTS  
`/*Comment out any length of text with forward slashes and astrisks. They may contain semicolons. You cannot nest these comments.*/  
Block comments should avoid being placed in columns 1 + 2 due to some SAS environments treating them as the end of the code.
2. COMMENT STATEMENTS  
`*Comment out a single sequence by including an asterisk at the front. The comment ends at the next semicolon.`  
Comment statements may be placed in columns 1 + 2, whatever that means.

Syntax Issues  
Some common syntax errors are misspelled keywords, missing semicolons, and invalid options.  
The SAS editor displays potential errors in code in Red.  
If a STEP sequence keyword (DATA or PROC) is misspelled, the statements following the keyword error as well—Since they are only supposed to follow in a data step, and the software sees them out on their own it flags them.  
If SAS encounters a Syntax error while running code, it logs the ERROR or WARNING to the log, along with an explanation. SAS does not execute code that has syntax errors in it, but moves onto the next one after the step boundary. 
- A Warning means that SAS was able to perform the action.  
- Errors are not performed.  

When you encounter errors in the log, check preceding statements to the error statement. If a semicolon is missing, the previous statement is probably running into the next one.  

Unbalanced Quotation Marks  
In SAS, a quotation counter keeps track of the number of quotation marks used. It expects an even number. When quotation marks are unbalanced, SAS does not read the statement that contains the quotation, and any that follow correctly.  
Purple text represents a quoted string.  
If the program keeps running without stopping, its probably a missing quotation mark.

Common syntax errors include invalid options, missing semicolons, unmatched quotation marks, and misspelled keywords.  
Although SAS allows either single or double quotation marks, you can’t mix the types. If you use one type to begin and a different type to end, SAS considers the quotation marks unbalanced.  

### Accessing Data   
- explain the concept of a SAS library
- state the difference between a temporary library and a permanent library
- assign a library reference name to a SAS library by using the LIBNAME statement
- explore the contents of SAS libraries using the CONTENTS procedure
- access a data set in a user-created permanent library
- define the components of a SAS data set
- browse the descriptor portion of a SAS data set using the CONTENTS procedure
- browse the data portion of a SAS data set using the PRINT procedure
- identify the two main types of values (character and numeric) and missing values
- explain the SAS naming conventions for variables and data sets

__SAS Libraries__  
SAS Libraries are an organizational structure where SAS stores its datasets.  Libraries are the highest level of organization.  
Each item in a library is referred to as a __Member__ of that library.  
At the beginning of each SAS session, SAS automatically provides a temporary and at least one permanent SAS Library for users to access by default.
*Work* is a temporary library that deletes its contents at session close.  
  
Data sets in permanent libraries remain after the SAS session is terminated.  
*Sashelp* and *Sasuser* are permanent libraries that are in the default configuration.  Sashelp contains example sets for reference.  

__Accessing SAS Libraries__  
The names of SAS Libraries are known by their Library Reference Names, or __Librefs__ for short. These librefs are links to the logical storage where the data files are located on the file system (regardless of using UNIX or Windows.)  
So: work, sasuser, and sashelp are librefs that refer to physical locations.  

__Two-Level Naming Structure__  
All SAS data sets have a two-level name that consists of the libref and the data set name, separated by a period. eg. sashelp/class

When a data set is in the the temporary work library, you can optionally use a one-level name. newsalestemps vs work.newsalestemps
When the data set is in a permanent library, you must use a two-level name. 
When you specify a one-level name, SAS assumes that the data set is stored in the work library. So, work is the default libref.
One-level names are temporary and will be deleted at the close of the session (Since theyre stored in work.)

Creating SAS Libraries
A user-created SAS library is permanent (unlike the default work library, which deletes its contents at the end of the session.)
A user-created SAS library resides in the OS's file system.
A user-created SAS library is also not automatically available in a SAS session. You must define the libref to make it availiable. 

Let’s look at how you define a library. First, you identify the location of the library to SAS.  
