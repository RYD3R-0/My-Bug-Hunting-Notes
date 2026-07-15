# HTTP

## My Mindset

When I intercept an HTTP request, I don't immediately think about payloads or vulnerabilities. I first try to understand how the application works.

## Things I look at first

* **HTTP Method:** Is the server enforcing the intended method, or will another method produce the same behavior?

* **Authentication:** How is the user identified? Is it using a session cookie, a Bearer token, or another mechanism?

* **Cookies:** Does the cookie only contain a session identifier, or does it expose user-controlled data?

* **Parameters:** Which values are controlled by the client? Which ones identify users or objects? Can they be modified, and how does the server handle these changes?

* **Endpoint:** What is the purpose of this endpoint? Does it look public, or should it require authentication or authorization?

---

## Request Analysis

Every request is a source of information.


> for every request I try to answer :

* What is this endpoint doing?
* What assumptions is the backend making?
* Which parts of the request does the server trust?
* Which parts can I control?
* How does the server validate the received data?

I also pay special attention to requests that change application state, such as:

* Updating user information.
* Changing permissions.
* Creating or deleting resources.
* Performing sensitive actions.

These endpoints usually require deeper testing because authorization issues and business logic flaws are more likely to appear.

---

## Headers

I try to understand the purpose of every important header.

I don't just look for the existence of headers like:

* Authorization
* Bearer tokens
* Cookies

I try to understand:

* Does the backend actually depend on this header?
* What happens if I modify or remove it?
* Is this header relevant for this specific endpoint?

Understanding why a header exists is more valuable than memorizing its name.

---

## Status Codes

Status codes are not just responses — they are clues.

Changes in status codes after modifying a request can reveal useful information about:

* Application behavior.
* Access control.
* Resource existence.
* Unexpected backend logic.

A response is not only an answer from the server; it is information that can help me understand how the application works.

---



## My Progress

This is what I understand about HTTP at this stage of my learning journey.

I will keep updating this note as my knowledge, methodology, and experience in web security improve.
