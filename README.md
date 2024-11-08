# Python
#Now we will add subject and make sure to address is visible along with body
#of email using email package


import smtplib     #simple mail transfer protocol
#mime -->Multi Purpose Internet Mail Extension Protocol
from email.mime.multipart import MIMEMultipart 
from email.mime.text import MIMEText

#defining data
From = "gssmanikanta002@gmail.com"  #give your email id
to = input("give receiver gmailid")
subject = "HI THIS IS MANI" #give your own subject
msg = MIMEMultipart()
msg['From'] = From
msg['To'] = to
msg['Subject'] = subject
body = "HOW ARE YOU " # The \n separates the message
msg.attach(MIMEText(body,'plain'))
text = msg.as_string()
#same usage of smtplib to start the process
server = smtplib.SMTP('smtp.gmail.com', 587)
server.starttls()
#Next, log in to the server
server.login(From, "glsjbopmmundwazo") #give your app passcode here 
#Send the mail
server.sendmail(From,to,text)
print("Mail Sent")
server.quit()
