# Authentication Flow

## How I Think About Authentication Flow

When analyzing authentication, I try to understand how the application moves from an unauthenticated state to an authenticated one.

I focus on the logic behind the flow:

* What requests actually change the authentication state?
* Are there multiple steps before the user is considered fully authenticated?
* Which step creates or confirms the authenticated session?
* Does the backend enforce every step, or is some of the flow only handled by the frontend?
* Can any step be skipped or manipulated?

---

## What I Learned

Authentication is not just "enter username and password".

It is the full process the application uses to decide whether a user is trusted or not.

That means I need to pay attention to every step, not only the password check.

If a step can be skipped, that is usually where the problem is.

---

## What I Keep Asking Myself

* Can I reach the next step without finishing the current one?
* Can I jump directly to a protected page?
* Is the frontend only pretending to enforce the flow?
* Does the backend actually care about the step I skipped?
* Is this really authentication, or just a redirect that looks secure?

---

## Lessons from the Labs

### Username Enumeration

Sometimes the problem appears before the password even matters.

Small differences in error messages, response size, or timing can leak whether a username exists.

That means the login flow itself can already give away useful information.

---

### 2FA

A 2FA page does not automatically mean the account is protected.

What matters is whether the backend really waits for the second step before marking the user as fully logged in.

If the session is already treated as authenticated too early, the extra page is just a fake barrier.

---

### Password Reset

Password reset is part of authentication too.

If the reset flow is weak, broken, or badly designed, I may not need to attack the login page at all.

That is why I do not treat password reset as a side feature.

---

## My Current View

What matters most to me is not whether the application has a login page.

What matters is whether the backend is actually enforcing the full authentication flow.

If the flow is broken, the account may be reachable without proving identity the right way.
