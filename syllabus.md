# Syllabus
  Hao Ye
  Health Science Center Libraries, University of Florida
  (updated: 2020-11-26)

## Intro
* Goals
  The goal of this workshop is to provide *practical* advice for research projects:
  * you can use these tips now
  * concepts and skills will scale to:
    - more complex projects
    - more collaborators
* Motivations
  Why should you care about this topic?
  --
  * organizing your projects and data will:
    - improve reproducibility
    - make the work more accessible for others
  --
    - **this includes yourself at a later point!**
* Learning Outcomes
  By the end of the workshop, participants will be able to:
  * implement recommended practices for file and folder organization in projects
  * use and apply file naming conventions
  * understand the principles of tidy data for structuring tabular data

## File and Folder Organization

* Principles
  * You don't want to spend time looking for stuff.
    - Your collaborators don't want to spend time looking for stuff either.
    - Keep project files in a single folder.
  * Document key decisions about the project.
    - You don't want your collaborators bugging you with easily-answered questions.
* Practices
  * Use sub-folders to organize data, figures, manuscript, etc.
    - separate raw and processed data
  * Maintain documentation on:
    - who did the experiments
    - what the format is for the data
    - when/how/why
* What Folders Do I Need?
  <pre class = "hljs remark-code">
  hye/
  ├── grants/
  ├── presentations_and_travel/
  ├── projects/
  ├── teaching/
  ├── vitae/
  └── websites/
  </pre>
  --
  When I want to {work/apply for money/fill out forms/etc.}, I know where to start.
* Inside a Project Folder
  <pre class = "hljs remark-code">
  project/
  ├── data/
  ├── figures/
  ├── output/
  ├── paper/
  ├── R/
  └── README.md
  </pre>
  --
  * more examples in [Marwick et al. 2018 "Packaging Data Analytical Work Reproducibly Using R (and Friends)"](https://www.tandfonline.com/doi/abs/10.1080/00031305.2017.1375986)
* A Project README
  * short summary of project &amp; goals
  * include guidance for the most common/important task
    - (software) how to install and run it
    - (paper) which file is the final report/paper
    - (data) the summary figure or main file
  * acknowledgments
  * how to cite the work
* Summary
  * for each project, store files and information together
    - don't rely on memory!
  * make it easy to use
    - **(avoids)** someone who would be interested not having the patience to engage
    - someone who *needs* specific details *will* go digging for it

## Naming Things

* Principles
  Choose file names that:
  * are machine-readable
  * are human-readable
  * play well with default ordering
* Examples (NOT SO GOOD)
  <pre class = "hljs remark-code">
  Drake's FILES with spaces and punctuation.xlsx
  01.R
  figure 1.png
  fig 2.png
  report-final FINAL HY-comments ver3.docx
  </pre>
* Examples (BETTER)
  <pre class = "hljs remark-code">
  drake_learned_about_underscores.xlsx
  01_import-data.R
  fig01_scatterplot_length-vs-interest.png
  fig02_histogram_talk-attendance.png
  report-on-DEC1_2020-06-01_HY-comments.docx
  </pre>
* Machine-Readable
  * Avoid spaces, punctuation, accented characters, mixing capital and lower-case.
    - computers and filesystems can struggle with these
    - easier names help people remember, too!
  * Use underscore `'_'` between metadata groups
  * Use hyphen `'-'` between words within groups
* Human-Readable
  * Use filenames that will help you find it later.
  * For code, use nouns for objects and verbs for actions:
    - e.g. `load-data.R`, `mtcars_measurements.csv`
* Using Default Ordering
  * Files are usually sorted alphabetically
    - we can make use of this!
  * Left-pad with numbers to order files:
    - e.g. `01_load-data.R`, `02_process-data.R`
  * Use ISO-8601 for dates:
    - `YYYY-MM-DD` format (when files are sorted alphabetically, this format makes the order chronological, too!)
  <img src="https://imgs.xkcd.com/comics/iso_8601_2x.png" width="60%" />
  [xkcd/1179](https://xkcd.com/1179/)
* Example
  <pre class = "hljs remark-code">
  siteA_2020-04-01_animal-count.xls
  siteA_2020-05-01_animal-count.xls
  siteB_2020-04-01_animal-count.xls
  siteB_2020-04-01_weather.dat
  siteB_2020-05-01_animal-count.xls
  siteB_2020-05-01_weather.dat
  </pre>
  --
  * files are organized by site
    - dates of data collection are visible
    - for a given site and date, types of measurement are clear
* Summary
  * you probably use names to organize files already!
    - these tips are intended to help improve your system
  * use a consistent scheme within each folder
    - use subfolders to help separate files with different purposes

## Structuring Tabular Data

* Principles
  Make it easy for anyone to work with your data:
  * Structure data for analysis (i.e. "Tidy Data")
  * Don't use spreadsheet-text-formatting to store data!
  * Keep raw data raw
  * Include a Data Dictionary
* Tidy Data
  Properties of *tidy data*:
  * each column is a variable
  * each row is an observation
  * each table is a single observational unit
* Common issues
  * data values are stored in column headers
    - e.g. treatment values, dates of sampling
  * multiple variables are stored in one column
  * some variables are stored in rows in addition to columns
  * "1 observational unit = 1 table" is violated
    - e.g. subject info and samples are stored in one table instead of separate tables with shared identifiers
* Column Labels are Values
  |name|Thin Mints|Samoas|Tagalongs|
  |--|--|--|--|
  |A|4|0|0|
  |B|2|0|2|
  |c|0|3|1|
* Column Labels Fixed
  |name|flavor|boxes|
  |--|--|--|
  |A|Thin Mints|4|
  |B|Thin Mints|2|
  |B|Tagalongs|2|
  |C|Samoas|3|
  |C|Tagalongs|1|
* Multiple Observational Units
  |name|address|flavor|boxes|
  |--|--|--|--|
  |A|3828 Piermont Dr|Thin Mints|4|
  |B|221B Baker St|Thin Mints|2|
  |B|221B Baker St|Tagalongs|2|
  |C|124 Conch St|Samoas|3|
  |C|124 Conch St|Tagalongs|1|
* Fixed Tables
  .pull-left[
  |name|flavor|boxes|
  |--|--|--|
  |A|Thin Mints|4|
  |B|Thin Mints|2|
  |B|Tagalongs|2|
  |C|Samoas|3|
  |C|Tagalongs|1|
  ]
  .pull-right[
  |name|address|
  |--|--|
  |A|3828 Piermont Dr|
  |B|221B Baker St|
  |C|124 Conch St|
  ]
* Spreadsheet Formatting
  * prefer empty cells or `'NA'` for missing data
    - *be careful about `'NA'` for certain types of data (e.g. country code for "Namibia")*
  * do NOT space out data with empty rows/columns
  * do NOT use text formatting (e.g. bold/italics) to store information
    - conditional formatting can help visualize
  * Excel LOVES to convert data into a date format
* Spreadsheet Example
  ![Figure 10 from Broman &amp; Woo "Data Organization in Spreadsheets", showing a data table with an outlier highlighted in red as an example of bad formatting, and then an alternative where the outlier status is encoded in its own column.](spreadsheet_formatting.png)
  Instead of highlighting the cells with outliers, encode outlier status as its own column.
* Raw Data
  * store raw data for reproducibility
    - e.g. if analysis tools change (as in bioinformatics workflows)
  * document processing steps in code or text
    - someone else can see what processing was done, and reproduce it
    - OpenRefine is a great tool for cleaning messy data (and records the steps for you)!
* Data Dictionary
  * define your rows and columns are
    - e.g. do rows correspond to:
       + individual subjects
       + OR data collection sessions
       + OR individual samples from a measurement device
  * define codes, categories, acronyms
  * define relationships between multiple tables
  * [more detail on metadata](https://guides.uflib.ufl.edu/datamanagement/metadata)
* Example Data Dictionary
  .compact-table[
  |name|plot_name|group|description|type|
  |--|--|--|--|--|
  |mouse|Mouse|demographic|Animal identifier|text|
  |sex|Sex|demographic|Male (M) or Female (F)|factor|
  |sac_date|Date of sac|demographic|Date mouse was sacrificed|date|
  |partial_inflation|Partial inflation|clinical|Indicates if mouse showed partial pancreatic inflation|logical|
  |coat_color|Coat color|demographic|Coat color, by visual inspection|factor|
  |crumblers|Crumblers|clinical|Indicates if mouse stored food in their bedding|logical|
  |diet_days|Days on diet|clinical|Number of days on high-fat diet|numeric|
  ]
  (modified from Figure 9 of Broman &amp; Woo "Data Organization in Spreadsheets")

## Thanks

* Contact me for additional questions or consultation requests!
* Check back in on the libguide for more modules and contact info:
  - https://guides.uflib.ufl.edu/reproducibility
