
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
		we user Referess token to generate a new Access token when every it