Readme.md
# Smoothcomp AWS Data Engineering Project
## Purpose
This project details the process ofbuilding an automated ETL pipeline to analyze jiu-jitsu event and match data from https://smoothcomp.com/ to populate Power BI dashboards.  

The dashboard attempts to answer questions such as 
* How many athletes compete in Jiu-Jitsu?
* How does the popularity compare between styles, age groups, and skill levels?
* How many competitions do athletes participate in? 
* Does additional competitions improve performance?

### Languages Used
- Python
- SQL
- M
- DAX

### Technologies Used
- Docker
- AWS Fargate
- AWS S3 
- AWS Athena + Glue
- Power BI
-  Github Actions
	
## Constructing ETL Process
### **E**xtract
The two types of web pages downloaded in this project are events and all matches within each event.

#### Events Web pages
The past events search page allows filtering results using the inputs on the page or using URL query parameters.  Results for each downloaded page will be limited to 
* Only in the USA
* Only jiu-jitsu style events
* Only 1 month at a time for organizational purposes

An example URL for the month of November 2025 is https://smoothcomp.com/en/events/past?countries=US&cg=1,3,4,7&startDate=2025-11-01&endDate=2025-11-30&page=1
Months may contain more than 40 events, so multiple pages may be saved.  Each extracted page will be saved with the format ***{YYYYMM}_{Page_Number}.html***.

#### Matchlist Web Pages
Each event has a distinct URL to the event, and every page of matches can be found from there. For example, event 12345 would have the first page of matches at https://smoothcomp.com/en/event/25853/schedule/matchlist?page=1
Each extracted page will be saved with the format 
***{YYYYMM}\_{Event_ID}\_{Page_Number}.html***.

### **T**ransform


