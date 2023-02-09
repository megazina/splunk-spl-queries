# Dashboard and Queries for Splunk User Analytics (basic)
Tested on Splunk Enterprise 9.0
v1.0

## Contains:
- Logins
- Duration of Sessions
- Details around Searches for one or multiple Splunk Users

### IMPORTANT:

Run on a SH, the user should have access to _internal, _audit indexes.
Dashboard code is for Dashboard Studio type (replace the whole thing)
If your searches return no results - try expanding the timeframe. If still no results - you don't have permissions for the _internal or _audit index or |rest command - find someone who has to run these dashboards.

### Exclude
It's currently manual list. To add Users to Exclude list you can specify in Token config, i.e. "*@idontwantthis.com"

### Include Users
It pulls the list of users from _audit index, excluding those mentioned in 'exclude' Token

### Logins
Includes successful logins, if you want to add Failed logins - just add info=failed if you want to look at failed

### User Sessions Duration
If returns no results - may need to modify REGEX for ID field:
` | rex field=id "https:\/\/127.0.0.1:8089\/(\w+\/)+(?<user>\w+)"    `

### UI interactions 
mostly stored in index=_internal sourcetype=splunkd_ui_access