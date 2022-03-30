# ICP Subscription Service 
ICP based Authentication/Authorization
- needs to be a public endpoint any non IC app can use

### Canister Registry
- the service needs to send a certain amount of ICP to Subscription Canister

### Password Creation
```
`/subscribe
	?service={service_ICP_address}
	&user={user_ICP_address}
	&username={username}
	&password={***}
```

### Authorizing User
```
 `/authorize
	?service={service_ICP_address}
	&username={username}
	&password={***}
```

- NOTE: username and password will likely be in the body of request

### Wallet Agnostic
- user sends ICP/BTC to a services wallet
- since ICP/BTC are public wallets you can read all transactions
- Subscription Canister lookups all transactions for service wallet
- the website using this service should only need an ICP/BTC address and call to authorize endpoint
- each website will have a unique ICP/BTC address
- the ICP/BTC address serves as the lookup table for username and password

### Security
- rate limit attacks by IP address
- think about security of endpoint because bots 
- worse case hack they can use service

### User Flow
1) Send ICP to service address
2) Create an Account with ICP address which sent ICP
3) Login to Account in whatever service using this as Auth 

### Service Flow
1) Register service address by sending ICP to Subscription Canister
