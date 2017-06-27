#Email from Python Script (Python 3)

Create email.html.

Add email to distributionlist.txt.

Add email server creds.

```python3
from __future__ import print_function
import time
import getquery

from email.mime.text import MIMEText
from email.mime.multipart import MIMEMultipart
from email.MIMEBase import MIMEBase
from email import Encoders

import smtplib

fromaddr = "from@email.com"
getadd = open("distributionlist.txt","r").read().split(";")
for each in getadd:
    toaddr = getadd

print ("To:" + str(toaddr))
print ("Fetching Query")

#Options to add html as attachment (Remove '##'s)
##part = MIMEBase('application', "octet-stream")
##part.set_payload(open("output.html", "rb").read())
##Encoders.encode_base64(part)
##part.add_header('Content-Disposition', 'attachment; filename="output.html"')

#get markup and put in body of email
body = email.html

#build email header
msg = MIMEMultipart()
msg['From'] = fromaddr
msg['To'] = str(toaddr).strip("[")
msg['Subject'] = "Email Subject"
msg.attach(MIMEText(body, 'html'))
##msg.attach(part)

#smtp details - change if not gmail
server = smtplib.SMTP('smtp.gmail.com', 587)

server.ehlo()
server.starttls()
server.ehlo()

#email server login info:
server.login("user@email.com", "password")

#convert header to string
text = msg.as_string()
server.sendmail(fromaddr, toaddr, text)

print ("Sending Email")
