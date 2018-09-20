```python
import smtplib

sender = 'senders_email@you.com'
receivers = ['receivers_email@them.net']

message = """From: Sender <senders_email@you.com>
To: Receiver <receivers_email@them.net>
Subject: Python code e-mail test

This is a test e-mail message that I sent with some Python code. Is it still cold outside? If it is they should 
just open the garage doors to keep the veggies cool. Anyway see you later.
"""
# will need to sign up for a new gmail account or some other web email account to make sure it is not connected to a personal
# account for obvious security reasons. If using gmail, will have to allow less secure apps to connect to G_suite apps.
# Also if doing so leave time for the security options to update or an error could continue to be recieved up to an hour
# after changing the settings.

smtpObj = smtplib.SMTP('smtp.gmail.com', 587)
ehlo = smtpObj.ehlo()
print(ehlo)
tls = smtpObj.starttls()
print(tls)
smtpObj.login(' g_suite_login ', ' specific_g_suite_access_code ')
smtpObj.sendmail(sender, receivers, message)         
print ("Successfully sent email")
smtpObj.quit() 
```
