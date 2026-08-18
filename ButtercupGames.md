# ButterCup Games Analysis - Splunk Project

## Project Overview

This project uses the Buttercup Games tutorial data from Splunk to practice with the platform. The tutorial data includes vendor, purchases, security and website traffic data.
The tutorial data is provided [here](https://help.splunk.com/en/splunk-enterprise/get-started/search-tutorial/10.4/part-1-getting-started/what-you-need-for-this-tutorial#Download_the_tutorial_data_files)

In the project, we will be doing the following:
- 5 dashboards
- 3 scheduled reports
- 3 alerts
- And some bonus points: macros, field aliases and drilldowns

## Tutorial
Once you've downloaded Splunk and created a web account on [Splunk Enterprise](https://www.splunk.com/en_us/form/sign-up.html?module=nav&redirecturl=https://www.splunk.com/en_us/download/splunk-enterprise.html), open Splunk on your [local host](http://localhost:8000/en-US/account/login?return_to=%2Fen-US%2F)  and enter the admin password created when you downloaded Splunk.

#### Step 1 - Ingest the data into Splunk

1. Download the tutorial data zip file to your local computer
2. In Splunk &rarr; Add Data &rarr; Upload &rarr; Upload data &rarr; Select file &rarr; select the zip file (unzipped) &rarr; Next
3. On the input Settings, on the Host section, change to segment in path &rarr; segment number `1`
4. Click `Review` then `Submit`

Using this method, you can upload all the files contained in the tutorial data at once, and the only index will be `main`. There will be 4 sourcetypes:

- `secure_2` - Security events
- `access_combined_wcookie` - website events
- `vendor_sales` - vendor and sales events
- `tutorialdata`

**!For the next steps, make sure to have time range = all time!**

### Step 2 - Create the dashboards
#### Site Visitor Trends
1. Go back to Search & Reporting, and search `index=*` with Time Range = ALL TIME, to verify that all the data is ingested and shows in search.
2. To create a buying trends dashboard, we're going to search for the product categories customers purchased and show the count for each one. Search SPL command:
```
index=main sourcetype=access_* status=200 action=purchase
| stats count by categoryId
| sort - count
```
3. On the visualisation view, change the chart to your preferred chart. For this one, a column chart seems more appropriate.
4. Next, click `Save as` &rarr; New Dashboard &rarr; Dashboard Title `Buttercup Games Analysis` and give it a description &rarr; Dashboard Studio &rarr; Panel Title `Buying Trends` &rarr; Save Dashboard

#### Site Visitor Trends
1. Go back to search for the SPL command:
```
index=main sourcetype=access_*
| timechart span=1h count
```
2. On the visualisation view, change the chart to your preferred chart. For this one, a line chart seems more appropriate.
3. Click `Save as` &rarr; `Existing Dashboard` &rarr; 
