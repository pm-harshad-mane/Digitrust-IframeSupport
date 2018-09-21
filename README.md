# DigiTrust-IframeSupport

# Problem
When publisher loads the DigiTrust library on top-frame of the page, the ad-tech partners executing in cross-domain iframes on the page are not able to access the DigiTrust library and are unable to retrieve the Digitrust Id. As many tags / user-syncup executes in iframes it makes Digitrust Id un-accessible for these partners.

# Solution
Above code example attempts to create a bridge between Top-frame and iframes that are trying to access Digitrust Id from top-frame.

# How it works
An extra code (mentioned in index.html) will be loaded with the DigiTrust library, this code will create a friendly-iframe with name "dtLocator" and will add a message event listener which will respond to postMessages coming from iframes to get DigiTrust Id. 

Any partner in cross-domain iframe, trying to access DigiTrust Id will implement/copy the function callDigitrustWhileInIframe (mentioned in iframe_2.html), this function will simply try to find the dtLocator iframe and will send a PostMessage to retrieve the DigiTrust Id, the function accepts a callback as an argument, this callback will execute upon retrieving the DigiTrust Id.

The iframe created for dt.html can also be named as dtLocator to avoid two iframes being created.

The solution is inspired from cmpLocator module from CMPs used in GDPR.

# How to use?
Assuming you already have a web server running on your machine on port 80.

Open terminal
Go to your web-server directory. Maybe /var/www/html
git clone https://github.com/pm-harshad-mane/Digitrust-IframeSupport.git
Above command will create a directory with name "Digitrust-IframeSupport"

Now edit "hosts" file on your machine with command, sudo vi /etc/hosts
Add following entries to "hosts" file and save the file
127.0.0.1       buzz.com
127.0.0.1       neon.com
127.0.0.1       zeon.com

To apply new DNS entries made in hosts file execute this command, sudo killall -HUP mDNSResponder
Now open http://buzz.com/Digitrust-IframeSupport/ in your browser
If new DNS entries are still not reflecting, then if you are using Chrome browser, open chrome://net-internals/#dns in your browser and click button "Clear host cache".

# Screenshot
![alt text](https://raw.githubusercontent.com/pm-harshad-mane/Digitrust-IframeSupport/master/ScreenShot.png)
