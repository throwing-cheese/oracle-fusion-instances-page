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
		"name": "Department of Carrots",
		"initials": "DOC",
		"emoji": "🥕",
		"url": "https://example.com/DepartmentofCarrots/",
		"wave": "3",
		"instances": [
			{ "url": "bird.aa.bb2", "label":"PROD"},
			{ "url": "bird-dev1.aa.bb2", "label":"DEV1"},
			{ "url": "bird-test.aa.bb2", "label":"TEST"}
		]}, {
		"name": "Fine Cheese Manufacturers",
		"initials": "FCM",
		"emoji": "🧀",
		"url": "https://example.com/DOC/",
		"wave": "n/a",
		"instances": [
			{ "url": "fa-long-saasfaprod1.fa.ocs", "label":"PROD"},
			{ "url": "fa-long-dev1-saasfaprod1.fa.ocs", "label":"DEV1", "cloned":"2022-12-05"}
		]}, {
		"name": "Gotham City Council",
		"initials": "GCC",
		"emoji": "🦁",
		"url": "https://example.com/FCM/",
		"wave": "1",
		"instances": [
			{ "url": "song.fa.em3", "label":"PROD"},
			{ "url": "song-test.fa.em3", "label":"TEST", "cloned":"2023-01-17" },
			{ "url": "song-dev2.fa.em3", "label":"DEV2", "cloned":"2023-01-30" },
			{ "url": "song-dev7.fa.em3", "label":"PREPROD", "cloned":"2022-06-23" },
			{ "url": "song-dev1.fa.em3", "label":"TRAIN", "cloned":"2022-11-29" }
		]}, {
		"name": "Incredibly Edible Bricks",
		"initials": "IEB",
		"emoji": "🐮",
		"wave": "3"
		}, {
		"name": "Gotham City Hospital",
		"initials": "GCH",
		"emoji": "🏥",
		"url": "https://example.com/GCH/Shared%20Documents/Managed%20Services",
		"wave": "2",
		"instances": [
			{ "url": "fa-ping-saasfaprod1.fa.ocs", "label":"PROD"},
			{ "url": "fa-ping-dev1-saasfaprod1.fa.ocs", "label":"DEV", "cloned":"2022-11-16" },
			{ "url": "fa-ping-test-saasfaprod1.fa.ocs", "label":"TEST", "cloned":"2022-11-17" }
		]}, {
		"name": "Fine Cheese Runners",
		"initials": "FCR",
		"emoji": "🏃",
		"url": "https://example.com/FCR/",
		"wave": ""
		}, {
		"name": "Cheesy Crate Express",
		"initials": "CCE",
		"emoji": "🎯",
		"url": "https://example.com/CCE/",
		"wave": "1",
		"instances": [
			{ "url": "fa-pong-saasfaprod1.fa.ocs", "label":"PROD"},
			{ "url": "fa-pong-dev1-saasfaprod1.fa.ocs", "label":"DEV", "cloned":"2022-06-10" },
			{ "url": "fa-pong-test-saasfaprod1.fa.ocs", "label":"TEST", "cloned":"2022-11-28" }
		]}, {
		"name": "Fromage Fresh Corp",
		"initials": "FFC",
		"emoji": "🥶",
		"url": "https://example.com/FFC/",
		"wave": "1",
		"instances": [
			{ "url": "hoop.fa.em3", "label":"PROD"},
			{ "url": "hoop-dev2.fa.em3", "label":"DEV2"},
			{ "url": "hoop-dev4.fa.em3", "label":"DEV4"},
			{ "url": "hoop-test.fa.em3", "label":"TEST"}
		]}, {
		"name": "Ricotta Ridge Express",
		"initials": "RRE",
		"emoji": "✅",
		"url": "https://example.com/RRE/",
		"wave": "3",
		"instances": [
			{ "url": "flat.fa.em1.zzz", "label":"PROD", "css":"PROD"},
			{ "url": "flat-dev1.fa.em1.zzz", "label":"DEV"},
			{ "url": "flat-test.fa.em1.zzz", "label":"TEST"}
		]}, {
		"name": "Stinky Cheese Association",
		"initials": "SCA",
		"emoji": "👃",
		"url": "https://example.com/SCA/",
		"wave": "3",
		"instances": [
			{ "url": "fa-golf-saasfaprod1.fa.ocs", "label":"PROD"},
			{ "url": "fa-golf-dev1-saasfaprod1.fa.ocs", "label":"DEV1"},
			{ "url": "fa-golf-test-saasfaprod1.fa.ocs", "label":"TEST"}
		]}, {
		"name": "Smelly Socks Champions",
		"initials": "SSC",
		"emoji": "🧦",
		"url": "https://example.com/SSC/",
		"wave": "3",
		"instances": [
			{ "url": "flit.fa.em1.zzz", "label":"PROD"},
			{ "url": "flit-test.fa.em1.zzz", "label":"TEST"}
		]}, {
		"name": "Pungent Cheddar Association",
		"initials": "PCA",
		"emoji": "🐈",
		"url": "https://example.com/PCA/",
		"wave": "1",
		"instances": [
			{ "url": "flot.fa.em3", "label":"PROD"},
			{ "url": "flot-dev2.fa.em3", "label":"DEV"},
			{ "url": "flot-test.fa.em3", "label":"TEST"},
			{ "url": "flot-dev5.fa.em3", "label":"TRAIN"}
		]}, {
		"name": "Metropolis City Council",
		"initials": "MCC",
		"emoji": "🍎",
		"url": "https://example.com/MCC/",
		"wave": "1",
		"instances": [
			{ "url": "able.fa.em3", "label":"PROD"},
			{ "url": "able-dev1.fa.em3", "label":"DEV1"},
			{ "url": "able-dev2.fa.em3", "label":"DEV2"},
			{ "url": "able-dev3.fa.em3", "label":"DEV3"},
			{ "url": "able-test.fa.em3", "label":"TEST"}
		]}
	]
 };
```

## Release Docs

For the main modules (Financials, Procurement, Projects, HCM, Payroll, Common), `What's New` Release Docs are shown in a table under the `Oracle Release Docs` heading, linking through to the release docs for release A, B, C and D for year year from 2019 through to current + 1 year (e.g. as of 6th December 2023, the release docs go up to Release 24D for 2024).

Useful as allows you to filter on module / year / release label to narrow down which set Release Docs to return.

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
		"parent_label": "ERP",
		"module_url_tag_1": "fin",
		"module_url_tag_2": "financials"
		},{
		"module_name": "Human Resources Cloud",
		"parent_label": "HCM",
		"module_url_tag_1": "ghr",
		"module_url_tag_2": "global-hr"
		},{
		"module_name": "Human Resources Helpdesk",
		"parent_label": "HCM",
		"module_url_tag_1": "hr-helpdesk",
		"module_url_tag_2": "hr-helpdesk"
		},{
		"module_name": "HCM Cloud Common",
		"parent_label": "HCM",
		"module_url_tag_1": "hcmcommon",
		"module_url_tag_2": "hcm-common"
		},{
		"module_name": "Oracle Common Technologies and User Experience",
		"parent_label": "Common",
		"module_url_tag_1": "common",
		"module_url_tag_2": "common"
		},{
		"module_name": "Payroll",
		"parent_label": "HCM",
		"module_url_tag_1": "payroll",
		"module_url_tag_2": "payroll"
		},{
		"module_name": "Procurement",
		"parent_label": "SCM",
		"module_url_tag_1": "proc",
		"module_url_tag_2": "procurement"
		},{
		"module_name": "Project Management",
		"parent_label": "ERP",
		"module_url_tag_1": "ppm",
		"module_url_tag_2": "ppm"
		},{
		"module_name": "Self Service Procurement",
		"parent_label": "SCM",
		"module_url_tag_1": "ssproc",
		"module_url_tag_2": "ssproc"
		}
	]
 };
```
