# Adapt Oakland Web
Adapt Oakland Web UI

## Description

Minimal React app built for Urban Biofilter's Adapt Oakland project. The aim is to present several years of urban design/environmental research through an interactive map that integrates with a varierty of charts, tables, case studies, and other information.

This data is grouped into many overlapping categories, so a system of 'tagging' is being used to arbitrarily relate the data. These tags are activated and deactivated by the UI menus to selectively query the content shown. 

Boilerplate borrowed (and modified) from: [https://github.com/Hyra/Frickle/](https://github.com/Hyra/Frickle/).

## Installation

### MacOSX:

Sync AO_Website folder on Google Drive.

(if you aren't working on the AdaptOakland project but using this repo for your own purposes, there is an importer - xlsx_2_db.js - which is set up to read a .xlsx with pointers to content to be imported to mongoDB. The format of this spreadsheet can be inferred from reading the importer code):

Install Homebrew.

Install Node Version Manager (NVM).

Install Heroku Toolbelt.

Install Git (if you don't already have it).

Install MongoDB using Homebrew:

`brew install mongo`

copy and paste the first two lines Homebrew suggests to run Mongo on login (and to launch it now)

Install NodeJS 0.12.7 using NVM. Then clone the repo and install dependencies:
```
nvm install 0.12.7
git clone https://github.com/johnvf/adapt-web-ui.git
cd adapt-web-ui
npm install -g gulp-cli
npm install
```
Place a .env file in your folder that contains the following keys 

(if you aren't working on the AdaptOakland project but using this repo for your own purposes, you will need to create a google service account and obtain these keys. The value of GAPI_PRIVATE_KEY needs to be surrounded by double quotes in order for the .env file to work correctly):
- GAPI_PRIVATE_KEY_ID
- GAPI_PRIVATE_KEY
- GAPI_CLIENT_EMAIL
- GAPI_CLIENT_ID
- GAPI_TYPE

Add the following to your .bashrc, changing paths as needed:

```
alias adaptweb="cd ~/Projects/adapt-web-ui; git pull; heroku local"
alias adaptdata="cd ~/Projects/adapt-web-ui; node ~/Projects/adapt-web-ui/xlsx_2_db.js ~/Google\ Drive/Adapt\ Oakland/AO_Website/AO_Master_spreadsheet.xlsx"
```

To run, type: 
```
adaptweb
```
Visit [http://localhost:8080](http://localhost:8080)

To run the importer, type:
```
adaptdata
```

### Windows:
Ensure you have Powershell 3

Install Git

Install Scoop

To be continued...

## API
The REST API routes are auto-generated by mers: https://github.com/jspears/mers

- To seed the database, run node seed_db
- Check out the '/seeds' folder for sample data, or use Postman to explore the API.
- Mers has support for filtering resources. 
- The following resources are supported:
  - asset
  - map
  - mapstyle
  - tabular
  - tag
  - text
  - user
- Try out the following on the sample data for an example of how multiple tags in the UI state could be concatenated to change the output of queries. NOTE: It seems that MERS only supports filtering on strings. Only 1 filter works.
  - http://localhost:8080/api/text
  - http://localhost:8080/api/text?filter[tags]=one_tag
