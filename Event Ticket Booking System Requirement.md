---
tags:
  - Requirement
---
### High level requirement

- users can browse events
- book tickets
- receive QR codes for validation
- leave likes and comment on the event page
- write updates or review on their own profile page, where user can also leave comments and likes.
- user can follow each other, if followed then they will see the reviews and updates of that user in the top. 
### High level requirement (Analysis)

- User will visits the website and authenticate
	- we will have 3 types users:
		- USER 
			- actions: browse events, book tickets, receive QR, leave likes and comment, write updates or review, follow user and events
		- ORGANIZER
			- actions: manage events
	- user will receive two [[JWT|Jwt Token]]
		- access token (exp 1 hour) 
		- refresh token (exp 10 days)
- user will see feed pages
	- here user can see the event reviews and updates (if user follows someone then their content will be shown first).
	- user can like see like
	- user can comment and see comments
- user will also see events page
	- here user can browse events
	- manage book event
		- after booking user will receive a QR code
	- leave like and see likes
	- leave comment and see comments
	- create a event (if user is ORGANIZER)
		- their are different types of events user can create
			- #TODO
- user will also see profile page
	- here we can view and manage user details
	- we can also view booked events and timings
- user can also view others profile by clicking on their profile name or handle name
	- where user will see their booked events, reviews and all updates