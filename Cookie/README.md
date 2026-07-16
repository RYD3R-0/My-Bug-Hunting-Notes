# Cookies

## My Mindset

When I see a cookie, I don't only look at its value.

The first question I ask is:

> What does this cookie represent, and how does the backend use it?

A cookie is not automatically trusted just because it is sent by the browser.

The important thing is understanding whether the backend treats it as:

* A simple identifier.
* Or actual user-controlled data.

---

## Things I Look At First

When analyzing cookies, I ask:

* Does the cookie contain only a session identifier?
* Does it contain user-related information such as roles, permissions, or user IDs?
* Is the value just a reference to data stored on the server?
* Does changing the cookie affect application behavior?

---

## Cookie vs Session

A cookie is only a mechanism used by the browser to store and send a value back to the server.

In many applications, the cookie contains only a session identifier.

The actual user state is stored on the server side, such as:

* Authentication status.
* User identity.
* Permissions.
* Roles.

The important distinction:

> Cookie = A value controlled and sent by the client
> Session = User state managed by the server

A secure design usually makes the session identifier only a reference, not a container for sensitive authorization data.

---

## Trust Boundary

The main question is not:

> "Is this value inside a cookie?"

The main question is:

> "Does the backend trust a value that the client can modify?"

Client-controlled data should always be treated carefully.

If I find values like:

```
role=user
isAdmin=false
user_id=123
```

inside cookies, I start asking:

* Is this value used for authentication or authorization?
* Does modifying it change my privileges?
* Does the backend validate it or blindly trust it?

---

## Identifier vs Data

A cookie like:

```
session=abc123
```

usually represents an identifier.

The server uses this identifier to find the real session data stored on the backend.

A cookie like:

```
user_id=123
role=user
```

contains actual application data controlled by the client.

The security impact depends on whether the backend relies on this data when making security decisions.

---

## Understanding Token Format

A value that looks random is not always a session ID.

For example:

```
session=eyJ1c2VyIjoiMTIzIiwicm9sZSI6InVzZXIifQ==
```

The format may indicate encoded data.

The important question is:

> Is this just an identifier, or does it contain readable/modifiable information?

If it contains important data, I should understand:

* Is it signed?
* Is its integrity verified?
* Can modifying it affect the application?

---

## Testing Mindset

When testing cookies, I don't immediately modify values randomly.

I first understand:

* What role does this cookie play?
* What behavior changes when it is modified?
* Is the backend making authorization decisions based on it?

The goal is not to change the cookie.

The goal is to discover whether the application trusts the wrong thing.

---

## My Progress

This is what I understand about Cookies at this stage of my learning journey.

I will keep updating this note as my knowledge, methodology, and experience in web security improve.
