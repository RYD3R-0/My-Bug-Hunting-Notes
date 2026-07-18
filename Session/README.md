# Sessions

## My Mindset

A session is not just something that keeps a user logged in.

It represents the user's identity and state on the server.

When I see a session, I don't think about the cookie first.

I think about what the backend knows about the user because of this session.

---

## How I Think About Sessions

A session is created only after the user successfully authenticates.

The browser only sends a session identifier.

The backend uses this identifier to locate the corresponding session and retrieve the user's state.

The important idea is:

> The browser proves *which session* it owns.

> The server decides *who that session belongs to*.

---

## What a Session Can Contain

Depending on the application, a session may contain information such as:

* User identity.
* Authentication state.
* Authorization data.
* User permissions.
* Login time.
* Last activity.
* Other application-specific state.

The important point is not **what** is stored.

The important point is that this information is managed by the server.

---

## Authentication, Session and Authorization

I think about them in this order:

Authentication

↓

Session is created

↓

The session identifies the current user

↓

Authorization decisions are made based on that identity

Understanding this flow helps me determine where a security issue actually exists.

---

## Session Hijacking

If an attacker obtains a valid Session ID, they usually do not need the victim's password.

The attacker is not bypassing authentication.

Instead, they are taking control of an already authenticated session.

This is why protecting Session IDs is critical.

---

## Testing Mindset

When testing sessions, I ask questions such as:

* How is the session created?
* How does the backend associate a session with a user?
* What happens if the Session ID changes?
* What happens if the Session ID is missing?
* Can a stolen Session ID be reused?
* When does the session expire or become invalid?

The goal is not simply to capture a Session ID.

The goal is to understand how the application manages user identity throughout the entire session lifecycle.

---

## My Progress

This is what I understand about Sessions at this stage of my learning journey.

I will keep updating this note as my knowledge, methodology, and experience in web security improve.
