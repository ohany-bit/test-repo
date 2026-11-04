---
name: business-knowledge
description: Business rules of Automation Exercise per area (Customer account / sign-up). Read before designing a test.
---

# Business knowledge - Automation Exercise
Modules: [Customer account](#customer-account) · end-to-end flows in scenarios.md.

## Customer account
Added 2026-11-04. Source: Signup / Login and Signup pages (seen), the app's published test cases 1-5 (document).
- A visitor becomes a shopper by signing up in two steps: name and email first, then account and address details.
- The email is the shopper's identity: it is fixed after the first step and cannot be used for a second account ("Email Address already exist!" - document).
- Required: Name, Email, Password, First name, Last name, Address, Country, State, City, Zipcode, Mobile Number.
- Optional: Title (Mr. / Mrs.), Date of birth, Company, Address 2, newsletter, partner offers.
- Country is one of India (default), United States, Canada, Australia, Israel, New Zealand, Singapore.
- Year of birth can be 1900 to 2021.
- After the account is made the shopper sees "ACCOUNT CREATED!" and is signed in ("Logged in as <name>") - document.
- A signed-in shopper can delete their own account ("ACCOUNT DELETED!") - document.
- Signing in needs the email and password; a wrong pair shows "Your email or password is incorrect!" (seen).
- No password length or format rule is shown on the page (not checked by submitting).
