
When you are tasked to run a penetration test against specific targets, as part of the passive recon phase, a service like [Shodan.io](http://www.shodan.io) can be helpful to learn various information about the clients network, without actively connecting to it. Furthermore, on the defensive side, you can use different services from Shodan.io to learn about connected and exposed devices belonging to your organization.

Shodan.io tries to connect to every device reachable online to build a search engine of connected "things" in contrast with a search engine for web pages. Once it gets a response it collects all the information related to the service and saves it in the database to make it searchable. Consider the saved record of one of tryhackme.com's servers.

![[Pasted image 20240704080510.png]]
This record shows a web server; however, as mentioned already, Shodan.io collects information related to any device it can find connected online. Searching for `tryhackme.com` on Shodan.io will display at least the record shown in the screenshot above. Through this we can learn:

- IP Address
- Hosting company
- Geographic location
- Server type and version

You may also try searching for the IP addresses obtained from DNS lookups, though these are more subject to change.

