# The Core Security Problem:

## Users Can Submit Arbitrary Input

### Here are some examples of submitting crafted input to achieve this objective:

- Changing the price of a product transmitted in a hidden HTML form field to fraudulently purchase the product for a cheaper amount
- Modifying a session token transmitted in an HTTP cookie to hijack the session of another authenticated user
- Removing certain parameters that normally are submitted to exploit a logic flaw in the application’s processing
- Altering some input that will be processed by a back-end database to inject a malicious database query and access sensitive data

Needless to say, SSL does nothing to stop an attacker from submitting crafted
input to the server. If the application uses SSL, this simply means that other users
on the network cannot view or modify the attacker’s data in transit. Because the attacker controls her end of the SSL tunnel, she can send anything she likes
to the server through this tunnel.

In a little over a decade, the World Wide Web has evolved from purely static
information repositories into highly functional applications that process sensitive
data and perform powerful actions with real-world consequences. During this
development, several factors have combined to bring about the weak security
posture demonstrated by the majority of today’s web applications.

# Core Defense Mechanisms

Most web applications handle access using a trio of interrelated security mechanisms:

- Authentication
- Session management
- Access control

When a user receives a token, the browser automatically submits it back to the server in each subsequent HTTP request, enabling the application to
associate the request with that user. HTTP cookies are the standard method for transmitting session tokens, although many applications
use hidden form fields or the URL query string for this purpose. If a user does
not make a request for a certain amount of time, the session is ideally expired.

## Approaches to Input Handling

- Reject Known Bad
- Accept Known Good
- Sanitization
- Safe Data Handling
- Semantic Checks
- Boundary Validation

### Boundary Validation

1. The application receives the user’s login details. The form handler validates
   that each item of input contains only permitted characters, is within a
   specific length limit, and does not contain any known attack signatures.
2. The application performs a SQL query to verify the user’s credentials.
   To prevent SQL injection attacks, any characters within the user input
   that may be used to attack the database are escaped before the query is
   constructed.
3. If the login succeeds, the application passes certain data from the user’s
   proﬁ le to a SOAP service to retrieve further information about her account.
   To prevent SOAP injection attacks, any XML metacharacters within the
   user’s proﬁ le data are suitably encoded.
4. The application displays the user’s account information back to the user’s
   browser. To prevent cross-site scripting attacks, the application HTMLencodes
   any user-supplied data that is embedded into the returned page.

## Handling Attackers

- Handling errors
- Maintaining audit logs
- Alerting administrators
- Reacting to attacks
