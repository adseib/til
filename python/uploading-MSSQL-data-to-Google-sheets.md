#Uploading SQL Query Data to Google Sheets (Python 3)

Leveraging Wesley Chun's excellent Google API [tutorial](http://wescpy.blogspot.ca/2016/06/using-new-google-sheets-api.html), the snipet below is a quick and dirty way to get an MSSQL query data on a GSheet.
pymsql does the heavy lifting on the MSSQL server side.

Get OAuth credentials here: https://developers.google.com/sheets/quickstart/python

Save .JSON in source folder.

Insert server info.

Insert query.

Insert spreadsheetID.

Start publishing.

```python
'''sheets-toys.py -- Google Sheets API demo
    created Jun 2016 by +Wesley Chun/@wescpy
    modified Oct 2016 by Andre Seib/@adseib
'''
from __future__ import print_function
import pymssql
import time


from apiclient import discovery
from httplib2 import Http
from oauth2client import file, client, tools

SCOPES = 'https://www.googleapis.com/auth/spreadsheets'
store = file.Storage('storage.json')
creds = store.get()

if not creds or creds.invalid:
    flow = client.flow_from_clientsecrets('client_secret.json', SCOPES)
    creds = tools.run_flow(flow, store)
SHEETS = discovery.build('sheets', 'v4', http=creds.authorize(Http()))


conn = pymssql.connect(server='', user='', password='', database='')
cursor = conn.cursor()
cursor.execute('SELECT * FROM ;')
rows = cursor.fetchall()
data = {'values': [row[:2] for row in rows]}

SHEETS.spreadsheets().values().update(spreadsheetId='SpreadsheetID',
    range='A1', body=data, valueInputOption='RAW').execute()
print('Wrote data to Sheet:')
rows = SHEETS.spreadsheets().values().get(spreadsheetId='SpreadsheetID',
    range='A1').execute().get('values', [])
for row in rows:
    print(row)
```
