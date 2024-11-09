Type 1 Hypervisor sits on top of Physical Hardware. The OS comes as a part of Hypervisor
Type 2 Hypervisor sits on top of OS on top of Physical Hardware.

BGP – is a routing protocol that allows routers to learn the routes and build the network map or routing table. Uses TCP port 179. Its Unicast. BGP is used because they scale and allows tunability. BGP has 4 messages they send.
OPEN – establish TCP sessions, exchange BGP version #, autonomous system number, hold time, BGP identifier (or ip address)
KEEP ALIVE – Health check.
UPDATE – when a new route is learnt, you tell the neighbor. Provides Network Layer Reachability Information (NLRI). Path attributes, withdrawn routes.
NOTIFICATION – anything goes wrong, the BGP sessions is closed.
 
BGP States à IDLE, CONNECT, ACTIVE, OPEN SENT, OPEN CONFIRM, ESTABLISHED
BGP Attributes à AS PATH is preferred as a rule. Next Hop. Weight.
Learn how BGP selects a path. There are multiple conditions where its tries to find a winner.
 
BGP will use the specific route first and then go with higher CIDR range (which is called a summary address)
Other way is to associate a weight with redundant routers, thus one will be preferred over other.
Other way is to associate a LOCAL_PREF number
Other way is to associate a AS PATH and if we want to have a route look ugly, we prepend it with the same AS # again. So two number will make it look ugly and will not be preferred.
Other way is modifying the MED.
 
BGP is easy way to engineer traffic.
 
