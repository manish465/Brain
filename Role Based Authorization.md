### Description

A [[Spring boot]] Backend that showcase Role Base Authorization, Whenever we hit a request, it will go to API Gateway and the API Gateway will check for Authentication and Authorization.
### Scope
- user management
	- add a user
	- view a user
	- update a user
	- delete a user
	- delete all user
- user auth
	- create JWT
	- verify JWT
	- verify Permission
	- user signup
	- user login
- school service
### System Description
The Role Based Authorization System will consist of multiple microservices that communicate through RESTful APIs. Each service will be responsible for a specific business domain and will have its own database to ensure loose coupling.
### System Architecture
System will have this following microservices:
- User Service
- School Service
- API Gatewa