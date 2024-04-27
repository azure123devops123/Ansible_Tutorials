# Blue Green Deployment Strategy: (Benefit: ZERO DOWN TIME ON PRODUCTION SERVERS - our applications are always available):

1) Green Group of Servers: These are actively running in the production environment and serving the users. These are live and accessible by our clients. (ACTIVE SERVERS)      --limit green

2) Blue Group of Servers: These are not actively running and serving the clients.  These are only being uses for new release. (PASSIVE SERVERS)                                 --limit blue

NOTE:- Once we have done with the new release on the blue servers then we will decommission (redirect all the traffic towards blue group of servers).