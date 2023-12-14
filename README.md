# Oracle Fusion Instances Page

## Introduction

Access all of your Fusion links from a single page.

If you support many customers, each of which might have 1 or more Fusion pods / instances, it's nice to be able to access them all from the same page.

Customer's data is stored in JSON format inside the HTML file. Edit that as per your requirements.

The idea behind this was to allow the customer data to be defined once, and then for the links to useful pages to be generated from that data, rather than having to write the URLs manually.

If you have a lot of customers, you can use the `filter customers` search box at the top of the list of customers to easily filter the list of instances.

## Demo

Demo [available here](https://throwing-cheese.github.io/demo/html/oracle-fusion-instances-page.html)

##  Top Level Menu

The page also contains links in the top menu to various Fusion Docs, grouped into headings:

- Oracle Support
- Cloud Customer Connect
- Explorer Training
- Cloud Docs
  - Userguides, FBDI Docs, Tables and Views, REST APIs
- Release Docs
  - Readiness
  - Opt In Info
  - Known Issues
  - Feature Listing Spreadsheet

## Instances Links

Each organisation for which JSON data is defined will have a block appear, such as:

![Sample instances block for a made up organisation](https://jimpix.co.uk/dist/images/github/oracle-fusion-instances-page/0001-block.png)

If the instance label is `PROD` then the table row for that instance will have a black background to make the PROD instances stand out.

The labels for the links are abbreviated to save space - meanings below, with made up Fusion URL (click `Headings Meanings` next to `Links` column heading to open pop-up window that provides an explanation of the headings):

- Home - Fusion Homepage (`https://xyz.oraclecloud.com/fscmUI/faces/FuseWelcome`)
- SQL - SQL Catalog Homepage (`https://xyz.oraclecloud.com/analytics/saw.dll?catalog`)
- S&M - Setup and Maintenance Homepage (`https://xyz.oraclecloud.com/fscmUI/faces/FuseTaskListManagerTop`)
- WL - BPM Worklist (`https://xyz.oraclecloud.com/integration/worklistapp/faces/home.jspx`)
- ADM - BPM Admin Home (`https://xyz.oraclecloud.com/integration/worklistapp/faces/administration.jspx?selectedAdminTab=administration`)
- TASKS - BPM Approval Tasks (`https://xyz.oraclecloud.com/integration/worklistapp/faces/administration.jspx?selectedAdminTab=taskConfig`)
- GPS - BPM Approval Groups (`https://xyz.oraclecloud.com/integration/worklistapp/faces/administration.jspx?selectedAdminTab=approvalGroup`)
- CS - Content Server (`https://xyz.oraclecloud.com/cs`)
- Img - Imaging Homepage (`https://xyz.oraclecloud.com/cs`)
- History - BI Publisher Job History (`https://xyz.oraclecloud.com/analytics/saw.dll?bipublisherEntry&Action=history`)

### Instances Links JSON

If you want to use the page for your own organisation, you can edit the JSON part of the file.

Each customer has 5 attributes:
- name
- initials
- emoji (added to help differentiate between instances)
- url
- wave
- instances
  - Each instance has 3 attributes:
	  - url
	  - label
	  - cloned (date cloned - optional - if populated, the clone age in days is displayed in light grey)

```javascript
// @@@@@@@@@@@@@@@@@@@@@@@@@@
// customer instances
// @@@@@@@@@@@@@@@@@@@@@@@@@@

// data for customers and customer instances

let data_customers = {
	"customers": [{
		"name": "Generic Corp One",
		"initials": "GCO",
		"emoji": "🔘",
		"url": "https://example.com/GCO/",
		"wave": "3",
		"instances": [
			{ "url": "gco", "label":"PROD"},
			{ "url": "gco-dev1", "label":"DEV1"},
			{ "url": "gco-test", "label":"TEST"}
		]}, {
		"name": "Generic Corp Two",
		"initials": "GCT",
		"emoji": "🔴",
		"url": "https://example.com/GCT/",
		"wave": "n/a",
		"instances": [
			{ "url": "gct", "label":"PROD"},
			{ "url": "gct-dev1", "label":"DEV1", "cloned":"2023-12-05"}
		]}, {
		"name": "Litter Picking Org",
		"initials": "LPO",
		"emoji": "✅",
		"url": "https://example.com/LPO/",
		"wave": "n/a",
		"instances": [
			{ "url": "lpo-dev1", "label":"DEV1", "cloned":"2023-10-18"}
		]}, {
		"name": "Tiny Town Council",
		"initials": "TTC",
		"emoji": "🟠",
		"url": "https://example.com/TTC/",
		"wave": "1",
		"instances": [
			{ "url": "ttc", "label":"PROD"},
			{ "url": "ttc-dev001", "label":"DEV001", "cloned":"2023-11-01" },
			{ "url": "ttc-dev002", "label":"DEV002", "cloned":"2023-11-02" },
			{ "url": "ttc-dev003", "label":"DEV003", "cloned":"2023-11-03" },
			{ "url": "ttc-dev004", "label":"DEV004", "cloned":"2023-11-04" },
			{ "url": "ttc-dev005", "label":"DEV005", "cloned":"2023-11-05" },
			{ "url": "ttc-dev006", "label":"DEV006", "cloned":"2023-11-06" },
			{ "url": "ttc-dev007", "label":"DEV007", "cloned":"2023-11-07" },
			{ "url": "ttc-dev008", "label":"DEV008", "cloned":"2023-11-08" },
			{ "url": "ttc-dev009", "label":"DEV009", "cloned":"2023-11-09" },
			{ "url": "ttc-dev010", "label":"DEV010", "cloned":"2023-11-10" },
			{ "url": "ttc-dev011", "label":"DEV011", "cloned":"2023-11-11" },
			{ "url": "ttc-dev012", "label":"DEV012", "cloned":"2023-11-12" }
		]}, {
		"name": "Expensive Widget Company",
		"initials": "EWC",
		"emoji": "🟡",
		"wave": "3",
		"instances": [
			{ "url": "ewc", "label":"PROD"},
			{ "url": "ewc-dev1", "label":"DEV1", "cloned":"2023-12-10" },
			{ "url": "ewc-dev3", "label":"DEV3", "cloned":"2023-09-22" }
		]}, {
		"name": "Gotham City Hospital",
		"initials": "GCH",
		"emoji": "🟢",
		"url": "https://example.com/GCH/",
		"wave": "2",
		"instances": [
			{ "url": "gch", "label":"PROD"},
			{ "url": "gch-dev1", "label":"DEV", "cloned":"2023-11-16" },
			{ "url": "gch-test", "label":"TEST", "cloned":"2023-11-17" }
		]}, {
		"name": "Express Crate Services",
		"initials": "ECS",
		"emoji": "🟣",
		"url": "https://example.com/ECS/",
		"wave": "1",
		"instances": [
			{ "url": "ecs", "label":"PROD"},
			{ "url": "ecs-dev1", "label":"DEV", "cloned":"2023-06-10" },
			{ "url": "ecs-test", "label":"TEST", "cloned":"2023-11-28" }
		]}, {
		"name": "Fresh Vegetables Corp",
		"initials": "FVC",
		"emoji": "⭕",
		"url": "https://example.com/FVC/",
		"wave": "1",
		"instances": [
			{ "url": "fvc", "label":"PROD"},
			{ "url": "fvc-dev2", "label":"DEV2"},
			{ "url": "fvc-dev4", "label":"DEV4"},
			{ "url": "fvc-test", "label":"TEST"}
		]}, {
		"name": "Precise Civil Engineering",
		"initials": "PCE",
		"emoji": "⏺️",
		"url": "https://example.com/PCE/",
		"wave": "3",
		"instances": [
			{ "url": "pce.fa.em1.zzz", "label":"PROD", "css":"PROD"},
			{ "url": "pce-dev1", "label":"DEV"},
			{ "url": "pce-test", "label":"TEST"}
		]}, {
		"name": "Fish Direct Ltd",
		"initials": "FDL",
		"emoji": "🟥",
		"url": "https://example.com/FDL/",
		"wave": "3",
		"instances": [
			{ "url": "fdl", "label":"PROD"},
			{ "url": "fdl-dev1", "label":"DEV1"},
			{ "url": "fdl-test", "label":"TEST"}
		]}, {
		"name": "Government Trade Contracts",
		"initials": "GTC",
		"emoji": "🟧",
		"url": "https://example.com/GTC/",
		"wave": "3",
		"instances": [
			{ "url": "gtc", "label":"PROD"},
			{ "url": "gtc-test", "label":"TEST"}
		]}, {
		"name": "Capable House Builders",
		"initials": "CHB",
		"emoji": "🟨",
		"url": "https://example.com/CHB/",
		"wave": "1",
		"instances": [
			{ "url": "chb", "label":"PROD"},
			{ "url": "chb-dev2", "label":"DEV"},
			{ "url": "chb-test", "label":"TEST"},
			{ "url": "chb-dev5", "label":"TRAIN"}
		]}, {
		"name": "Gotham City Services",
		"initials": "GCS",
		"emoji": "🟦",
		"url": "https://example.com/GCS/",
		"wave": "1",
		"instances": [
			{ "url": "gcs", "label":"PROD"},
			{ "url": "gcs-dev1", "label":"DEV1"},
			{ "url": "gcs-dev2", "label":"DEV2"},
			{ "url": "gcs-dev3", "label":"DEV3"},
			{ "url": "gcs-test", "label":"TEST"}
		]}
	]
 };
```

## Release Docs

For the main modules (Financials, Procurement, Projects, HCM, Payroll, Common), `What's New` Release Docs are shown in a table under the `Oracle Release Docs` heading, linking through to the release docs for release A, B, C and D for year year from 2019 through to current + 1 year (e.g. as of 6th December 2023, the release docs go up to Release 24D for 2024).

Useful as allows you to filter on year / release label to narrow down which set Release Docs to return.

### Release Docs JSON

The Release Docs table is held in JSON format - edit as required if you want to add / delete modules:

```javascript
// @@@@@@@@@@@@@@@@@@@@@@@@@@
// oracle release docs
// @@@@@@@@@@@@@@@@@@@@@@@@@@

// data for modules in a release

let data_modules = {
	"modules": [{
		"module_name": "Financials",
		"label": "FIN",
		"module_url_tag_1": "fin",
		"module_url_tag_2": "financials"
		},{
		"module_name": "Procurement",
		"label": "PROC",
		"module_url_tag_1": "proc",
		"module_url_tag_2": "procurement"
		},{
		"module_name": "Project Management",
		"label": "PPM",
		"module_url_tag_1": "ppm",
		"module_url_tag_2": "ppm"
		},{
		"module_name": "Oracle Common Technologies and User Experience",
		"label": "Common",
		"module_url_tag_1": "common",
		"module_url_tag_2": "common"
		},{
		"module_name": "Human Resources Cloud",
		"label": "HCM",
		"module_url_tag_1": "ghr",
		"module_url_tag_2": "global-hr"
		},{
		"module_name": "Payroll",
		"label": "PAYROLL",
		"module_url_tag_1": "payroll",
		"module_url_tag_2": "payroll"
		},{
		"module_name": "HCM Cloud Common",
		"label": "HCM-Common",
		"module_url_tag_1": "hcmcommon",
		"module_url_tag_2": "hcm-common"
		}
	]
 };
```
