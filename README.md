# Digitrust-IframeSupport

# How to use?
Assuming you already have a webserver running on your machine on port 80.

Open treminal
Go to your web-server directory. May be /var/www/html
git clone https://github.com/pm-harshad-mane/Digitrust-IframeSupport.git
Above command will create a directory with name "Digitrust-IframeSupport"

Now edit hosts file on your machine with command, sudo vi /etc/hosts
Add following enteries to hosts file and save the file
127.0.0.1       buzz.com
127.0.0.1       neon.com
127.0.0.1       zeon.com

To apply new DNS entries made in hosts file run this command, sudo killall -HUP mDNSResponder
Now open http://buzz.com/Digitrust-IframeSupport/ in your browser
If new DNS entries are still not reflecting then open chrome://net-internals/#dns in your browser and click button "Clear host cache"
