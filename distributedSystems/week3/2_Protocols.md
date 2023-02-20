# Protocols
* A definition of a set of rules for how 2 or more objects should interact with each other.

## HyperText Transfer Protocol
* Used for communication between clients and web servers.
* Are stateless hence all requests are independent transactions.

## Email
* Has the expectation that an email is only at one place at one time.
* Uses `SMTP`, a text based protocol that is connection based to send mail to inboxes.
	* Connection based allows it to relay information about multiple emails at once before explicitly terminating the connection.
* Uses `POP3` to organise and access messages by the recipient of the mail.