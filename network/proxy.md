# Proxy Server

- in short, a proxy server takes all incoming requests from a client computer and performs actions based on configured rules
- this can be filtering websites or apps that the network shouldn't have access to
- proxies can also hide or obfuscate a user's location by reporting they are somewhere other than they actually are
- proxies can handle multiple users or connections and act accordingly

## Why?

- proxies are helpful for keeping data from being sent improperly
- users cannot access harmful websites if a blacklist is established within the proxy
- build a cache inside the proxy that connections will pull from on each subsequent request
- log web requests
- bypass region locking features by reporting location inside a different region
- block ads

## VS. VPNs

- proxies only handle internet traffic
- VPNs handle **all** network traffic, so something like file sharing or messaging protocols

## Forward Proxies

- these are the proxies that accept all incoming requests from user and handle appropriately
- for example a request to a website, will be intercepted by the proxy and then either denied or redirected/forwarded with the proper headers configured

## Transparent Proxies

- they send all information, but the ip address is the proxy address
- useful for getting around ip address bans, but once the proxy ip is banned, same situation

## Anonymous Proxies

- will not pass user's ip address along
- will report themselves as a proxy
- useful for keeping ad tracking from building report on users

## More Anonymous Proxies

- they won't pass user information
- change their ip address so that they can't be tracked the same as other proxies

## Distorting Proxy

- passes an ip address, but that address is actually fake, it distorts the truth

## Residential Proxy

- uses a real ip address with a real machine, so it looks like an actual client, but it's still a proxy

## Data Center Proxy

- a proxy that uses a generated ip address in the cloud
- being a proxy from a data center, their connections tend to be faster and more reliable

## Public Proxy

- the least secure
- hackers can figure out what proxy users are on and target exploits
- could crash at any moment as they are usually not as well maintained
- can be difficult to know who actually maintains proxy, the unknown factor

## Private Proxy

- these are thought of as more reliable than public proxies
- however, they don't mean that traffic is private from the outside world or exploits
- its more of an access control setting, who can actually use the proxy vs. the public

## Dedicated Proxy

- multiple clients cannot access the proxy at the same time
- one client, one proxy
- just like private proxies, comes down to who has access to dedicated proxy

## Shared Proxy

- multiple clients can access
- usually providers will share resources to maintain proxy
- can handle lots of requests at the same time
- performance could be lower as multiple actions are being performed simultaneously

## Rotating Proxy

- each new client connection changes the ip address of the proxy
- no two clients will have the same ip address from the proxy
- can provide more security as addresses are not reused, and therefore cannot be as easily tracked

## SSL Proxy

- secures requests sent via SSL protocol, helps mitigate man in the middle attacks
- traffic is sent encrypted vs plain text

## Reverse Proxy

- hides the ip address of the requested server
- helps obfuscate the physical server's ip address, which can help keep vulnerabilities down and traffic from flooding
- also can provide cached versions of files to large groups of users making simultaneous requests to the same resources

## Sources

- [What is a Proxy Server? In English, Please.](https://www.freecodecamp.org/news/what-is-a-proxy-server-in-english-please/)
