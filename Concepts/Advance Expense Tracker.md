---
tags:
  - project
link: https://whimsical.com/advance-expense-tracker-AH847B4squjCENLmxitMa5
---
## Requirement
- user should be able to sign up, login
- user can view their profile
- user can add delete edit expense
- on receiving a transaction SMS in users phone it will be automatically added as expense

## HLD

![[Pasted image 20250218232726.png]]

## Database relation
![[Pasted image 20250218232740.png]]
### Service
- Auth Service: 
	- /signup (POST)
	- /login (POST)
	- /auth (GET)
- User Service:
	- /create {POST}
	- /get {GET}
	- /update {PUT}
	- /delete {DELETE}
- ML Service
	- /message {POST}
- Expense Service
	- /add {POST}
	- /get
	- /update
	- delete