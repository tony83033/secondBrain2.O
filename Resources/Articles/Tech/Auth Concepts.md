
Basic Auth Methods

1) Basic
		Add a Header Authorization: Basic <base64> encoded "username:password"
2) Digest
		Add a Header Authorization: Digest <md5 hash> 
3) API keys
		APIKEY or X-API-KEY we generate it for every user and store it to DB
4) Session
		we first store the session in redis and return the cookie we store it in client side and client send request with cookie we validate it with session 
			it's a a statefull method

Token Based Auth
1) Bearer and JWT Tokens
		Add Headers Authorization: Bearer <jwtToken>

2) Access and Refress Token
	Access token are sort live and used for API server
		Referess token long live
		we user Referess token to generate a new Access token when every it expiress
		We should always store Referess token in httOnlyCookie

OAuth2 and OICD
	 It's a Authorization framework not a Auth method
	 if I want to great a app to read the google drive 

SSO
SSO is a user expirence 
use saml protocal or OIDC protocal


========================================
Access Control
1) RBAC (Role-Based Access Control)
2) ABAC (Attribute Based Access Control)
3) ACL (Access Control List)
