#OAuth 2 implementation notes for webapi

##JWT
- Now a standard
- Data structure containing infomation about the issuer and subject (claims)
- Signed (tamper proof and authenticity)
- Are expireable
- JSON encoded
- symmetric + asymmetric sigs & symmetric + asymmetric encryption


###JWT:Header
- meta infomation
- algorithms & keys used

###JWT:Claims
- issuer (iss)
- audience (aud)
- issuedAt (iat)
- expiration (exp)
- subject (sub)
- ... application defined claims

##OAuth2
Controlling of access to resources on a web server.
Delegated authorisation (access tokens) whilst taking multiple client architectures,
with clients that have varying trust levels.

###OAuth2:Flows
- Authorisation Code Flow
    - Web Application Clients
        - Request Authorisation
        - Request Token
        - Access resources
- Implicit Flow
    - Native/Local Clients
        - Request Authorisation & Token
        - Access resource


####OAuth2:Flows:Authorisation Code Flow
Used in web apps where the web client/application is able to securely contact the authorisation
server. (Server rendered applications)
The access token would usually contain the issuer, signature and expiration.
Typical claims for a token would be:
 - resource owner identifier
 - client identifier (the application)
 - granted scopes (i.e the resources they have access to)

 Useful parts of this flow,
 - the access token for the application is never leaked to the browser
 - Long lived access can be implemented (i.e granular resource permissions)

####OAuth2:Flows:Implicit Flow
Used for local & native applications such as mobile apps and JS based applications.

Client app will call auth server, usually the authorise endpoint, including the:
- client id 
- the scope to access
- the redirect uri
- the response type
- the state

The server will then callback with some other properties:
- the access token
- expiration date
- the state

The client app will then be able to use that access token as the value of the bearer
header to retrieve the protected resources on the server.





