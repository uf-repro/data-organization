# Syllabus

## Intro

* Goals
  - *practical* advice for research projects:
  - you can use these tips now
  - concepts and skills will scale to:
    + more complex projects
    + more collaborators
* Motivations
  - organizing your projects and data will:
    + improve reproducibility
    + make the work more accessible for others
    **including yourself at a later point!**
* Learning Outcomes
  - describe and apply principles for organizing and naming files and folders
  - employ the concept of tidy data for structuring tabular data
  - import and view tabular data in R

## File and Folder Organization

* Principles for Organization
  - You don't want to spend time looking for stuff.
    + Using a consistent system establishes habits.
  - Keep all files related to a project in a single folder.
  - Include a project README file that describes the project.
  - Separate sub-folders for raw data, processed data, code, figures.
* General Folders I have
  - `grants/`
  - `presentations_and_travel/`
  - `projects/`
  - `vitae/`
  - `websites/`
* Example Project in R
  ```  
  project/
  ├── data/
  ├── figures/
  ├── output/
  ├── paper/
  ├── R/
  ├── README.md
  ```
  - more examples in [Marwick et al. 2018 "Packaging Data Analytical Work Reproducibly Using R (and Friends)"](https://www.tandfonline.com/doi/abs/10.1080/00031305.2017.1375986)

## Naming Things

* Principles
  - file names should:
    + are machine-readable
    + are human-readable
    + play well with default ordering
* Examples (NOT SO GOOD)  
  ```
  Drake's FILES with spaces and punctuation.xlsx
  figure 1.png
  fig 2.png
  report on DEC1 final FINAL HY-comments ver3.docx
  ```
* Examples (GOOD)
  ```
  drakes-files-are-getting-better.xlsx
  fig01_scatterplot_length-vs-interest.png
  fig02_histogram_talk-attendance.png
  report-on-DEC1_2020-06-01_HY-comments.docx
  ```
* Machine-Readable
  - Avoid spaces, punctuation, accented characters, mixing capital and lower-case.
    + different computers and filesystems struggle with these
    + using simpler names help to remember how it's spelled
  - Use underscore `'_'` to separate grouping levels.
  - Use hyphen `'-'` to separate words within a level.
* Human-Readable
  - Use filenames that will help you find it later.
  - Use nouns for objects, use verbs for actions:
    + e.g. `load-data.R`, `mtcars_measurements.csv`
* Using Default Ordering
  - Files are usually sorted alphabetically
    + we can make use of this!
  - Left-pad with numbers to order steps in a sequence:
    + e.g. `01_load-data.R`, `02_process-data.R`
  - Use ISO-8601 for dates:
    + `YYYY-MM-DD` format (when files are sorted alphabetically, this format makes the order chronological, too!)
* Example
  ```
  site-A_2020-04-01_animal-count.dat
  site-A_2020-05-01_animal-count.dat
  site-B_2020-04-01_animal-count.dat
  site-B_2020-04-01_weather.dat
  site-B_2020-05-01_animal-count.dat
  site-B_2020-05-01_weather.dat
  ```
  - files are organized by site
    + dates of data collection are visible
    + for a given site and date, types of measurement are clear
    
## Structuring Tabular Data

* Principles
  - Make it easy for anyone to work with your data:
    + Structure data for analysis (i.e. "Tidy Data")
    + Don't use spreadsheet-formatting to store data!
    + Keep raw data raw
    + Include a Data Dictionary
* Tidy Data
  - each column is a variable
  - each row is an observation
  - each table is a single observational unit
* Common issues
  - data values are stored in column headers
    + e.g. treatment values, dates of sampling
  - multiple variables are stored in one column
  - some variables are stored in rows in addition to columns
  - "1 observational unit = 1 table" is violated
    + e.g. subject info and samples are stored in one table instead of separate tables with shared identifiers
* Example (untidy data)
  - years of measurement as column headers
  <table class="table table-striped">
 <thead class="thead-dark">
  <tr>
   <th style="text-align:left;"> country </th>
   <th style="text-align:left;"> continent </th>
   <th style="text-align:right;"> 2002 </th>
   <th style="text-align:right;"> 2007 </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> Canada </td>
   <td style="text-align:left;"> Americas </td>
   <td style="text-align:right;"> 31902268 </td>
   <td style="text-align:right;"> 33390141 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Chile </td>
   <td style="text-align:left;"> Americas </td>
   <td style="text-align:right;"> 15497046 </td>
   <td style="text-align:right;"> 16284741 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Italy </td>
   <td style="text-align:left;"> Europe </td>
   <td style="text-align:right;"> 57926999 </td>
   <td style="text-align:right;"> 58147733 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Sudan </td>
   <td style="text-align:left;"> Africa </td>
   <td style="text-align:right;"> 37090298 </td>
   <td style="text-align:right;"> 42292929 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Thailand </td>
   <td style="text-align:left;"> Asia </td>
   <td style="text-align:right;"> 62806748 </td>
   <td style="text-align:right;"> 65068149 </td>
  </tr>
</tbody>
</table>

* Examples (tidy data)
  - years of measurement as its own column
  <table class="table table-striped">
 <thead class="thead-dark">
  <tr>
   <th style="text-align:left;"> country </th>
   <th style="text-align:left;"> continent </th>
   <th style="text-align:right;"> year </th>
   <th style="text-align:right;"> pop </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;"> Canada </td>
   <td style="text-align:left;"> Americas </td>
   <td style="text-align:right;"> 2002 </td>
   <td style="text-align:right;"> 31902268 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Canada </td>
   <td style="text-align:left;"> Americas </td>
   <td style="text-align:right;"> 2007 </td>
   <td style="text-align:right;"> 33390141 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Chile </td>
   <td style="text-align:left;"> Americas </td>
   <td style="text-align:right;"> 2002 </td>
   <td style="text-align:right;"> 15497046 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Chile </td>
   <td style="text-align:left;"> Americas </td>
   <td style="text-align:right;"> 2007 </td>
   <td style="text-align:right;"> 16284741 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Italy </td>
   <td style="text-align:left;"> Europe </td>
   <td style="text-align:right;"> 2002 </td>
   <td style="text-align:right;"> 57926999 </td>
  </tr>
  <tr>
   <td style="text-align:left;"> Italy </td>
   <td style="text-align:left;"> Europe </td>
   <td style="text-align:right;"> 2007 </td>
   <td style="text-align:right;"> 58147733 </td>
  </tr>
</tbody>
</table>

* Spreadsheet Formatting
  - prefer empty cells or `'NA'` for missing data
    + *be careful about `'NA'` for certain types of data (e.g. country code for "Namibia")*
  - do NOT space out data with empty rows/columns
  - do NOT use text formatting (e.g. bold/italics) to store information
    + conditional formatting can help visualize
  - Excel LOVES to convert data into a date format

* Raw Data
  - store raw data for reproducibility
    + e.g. if analysis tools change (as in bioinformatics workflows)
  - document processing steps in code or text
    + someone else can see what processing was done, and reproduce it
* Data Dictionary
  - define your rows and columns are
    + e.g. do rows correspond to:
      + individual subjects
      + OR data collection sessions
      + OR individual samples from a measurement device
  - define codes, categories, acronyms
  - define relationships between multiple tables
  - [more detail on metadata](https://guides.uflib.ufl.edu/datamanagement/metadata)

## Reading Data into R

* Basics of R and RStudio
  - [R](https://cran.r-project.org/) is the programming language
  - [RStudio](https://rstudio.com/) is *optional* software that provides an interface to working in R
    + **highly recommended** unless you have strong preferences and experience doing programming in a different environment
    + you probably want the [free Desktop version](https://rstudio.com/products/rstudio/download/#download)
* R Packages
  - The functionality of R is extended by *packages*:
  - open-source, developed by community members
  - packages vary in scope, e.g.
    + color themes from Wes Anderson movies
    + tools for making interactive web applications
* Ways to Get Data into R
  - datasets included with R and packages
    + `data()`
  - read in data files
    + comma-separated values (`.csv`) tables
    + R binary formats (`.Rdata`, `.Rda`, `.RDS`)
  - directly from Google Sheets -- [`googlesheets4`](https://googlesheets4.tidyverse.org/) package
  - directly from Excel -- [`readxl`](https://readxl.tidyverse.org/) package
* Demo (reading in CSV)
  ```r
  url <- "https://raw.githubusercontent.com/uf-repro/data-organization/master/data/gapminder_demo.csv"
  download.file(url, "data/gapminder_demo.csv")
  
  dat <- read.csv("data/gapminder_demo.csv")
  ```
* Demo (`googlesheets4`)
  ```r
  # install.packages("googlesheets4")
  library(googlesheets4)
  
  gs4_deauth() # don't authenticate, we just want to read a publicly-visible document
  
  dat <- read_sheet("https://docs.google.com/spreadsheets/d/16apE3bvGjPqyeXqWUnKgBlvGxi7GoJ4_T8OzHpYRA4k/edit?usp=sharing")
  ```
* Demo (`readxl`)
  ```r
  url <- "https://raw.githubusercontent.com/uf-repro/data-organization/master/data/gapminder_demo.xlsx"
  download.file(url, "data/gapminder_demo.xlsx")
  
  # install.packages("readxl")
  library(readxl)
  
  dat <- read_excel("data/gapminder_demo.xlsx")
  ```

## Thanks
* Contact me for additional questions or consultation requests!
* Check back in on the libguide for more modules and contact info:
  - https://guides.uflib.ufl.edu/reproducibility
