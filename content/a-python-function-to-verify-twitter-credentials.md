{
    "categories": [
        "Python", 
        "programming", 
        "Twitter", 
        "pycurl"
    ], 
    "date": "2009-04-03T19:09:25", 
    "tags": [
        "Python", 
        "programming", 
        "Twitter", 
        "pycurl"
    ], 
    "title": "A Python Function to Verify Twitter Credentials"
}

Thought I'd post this for the future generations, since I had a hard time finding a template anywhere on the web when I needed one. It's nothing revolutionary, but a useful snippet nonetheless. This is for one of my projects this semester.<code lang="python">import pycurl
def verifyTwitterCredentials(username, password):
    c = pycurl.Curl()
    c.setopt(c.URL, 'http://twitter.com/account/verify_credentials.xml')
    c.setopt(c.USERPWD, username + ":" +  password)
    twitterfeed = c.perform()

    status = c.getinfo(c.HTTP_CODE)

    if str(status) == '200':
        verified = True
    else:
        verified = False

    c.close()

return verified</code>