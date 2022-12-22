# Other Trainings

## OAuth 2.0

- OAuth Terminology
  - Resource Owner
    - User sitting in front of screen
  - Client
  - Authorization Server
  - Resource Server
  - Authorization Grant
    - There are different types
  - Access Token
- Ex:  Yelp requesting access to your google contacts
  - Resource Owner
    - The human behind the keyboard
  - Client:  Yelp
  - Authorization Server:  accounts.google.com

## Networking

- OSI Layers
  - Please Do Not Throw Sausage Pizza Away
    - Physical
    - Data Link
    - Netwok
    - Transport
    - Session
    - Presentation
    - Application
- Gateway vs Proxy
  - Both a proxy server and a gateway route traffic from inside a network to the Internet. A gateway, however, is more like a door to get to the Internet, while a proxy server acts like a wall that bars the inside of the network from being exposed to the Internet. A proxy server filters which connection is allowed, while a gateway doesn't do any filtering.
    - Gateways
      - For two networks to communicate, a gateway must be provided from each network. The gateway defines what is internal to the network and what is external. If a computer needs to communicate with another computer outside the network, it must be configured with a gateway to gain access outside the network. Without a gateway, a computer will be unable to get out, like someone locked inside a house.
    - Proxies
      - A proxy server represents the network from the outside. Any user trying to gain access to any computer inside a network with a proxy will only see the IP address of the proxy server. It acts like a barrier to hide your network by configuring the Internet options of computers within the network to first point to the proxy server before going out to the Internet. It keeps computers inside the network anonymous.

## References

- OAuth 2.0 and OpenId Connect
  -  https://www.okta.com/openid-connect/