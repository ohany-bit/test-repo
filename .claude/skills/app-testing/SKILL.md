---
name: app-testing
description: How to test Automation Exercise (automationexercise.com) - pages, login and sign-up flow, roles, environments, quirks and test ideas. Read before writing a web test for this app.
---

# Automation Exercise - app testing notes
Learned 2026-11-04 (focus: Signup). Only the Signup / Login part was walked.

## Environments
| Env | Web | API |
|---|---|---|
| Test | https://www.automationexercise.com/ | https://automationexercise.com/api/ (see api-catalog) |

## Stack
- Classic server-rendered web shop (full page posts, CSRF hidden field in every form). No XHR for sign-up/login.
- Bootstrap layout, English only, left-to-right. No language switch seen.
- Most inputs carry a `data-qa` attribute - use it first (stable, one match each).

## Main menu (top bar, all pages)
Home `/` · Products `/products` · Cart `/view_cart` · Signup / Login `/login` · Test Cases `/test_cases` ·
API Testing `/api_list` · Video Tutorials (external) · Contact us `/contact_us`.
After login the bar shows "Logged in as <name>", Logout and Delete Account (from the app's published cases - not seen, see Quirks).

## Pages (Signup part)
### Signup / Login - `/login`
Purpose: sign in, or start a new sign-up. Two forms side by side.
- Left "Login to your account": Email Address, Password, Login button. Wrong values -> red text "Your email or password is incorrect!" under the form (page reloads at /login).
- Right "New User Signup!": Name, Email Address, Signup button. Both required (browser check); email must look like an email.
- Existing email -> "Email Address already exist!" (from the app's published Test Case 5, not seen).
- Footer "Subscription" email box on every page - not part of sign-up.
### Signup - `/signup` (after the Signup button)
Purpose: second step - "Enter Account Information" and "Address Information".
- Title radio Mr. / Mrs. (optional), Name * (pre-filled), Email * (pre-filled, disabled), Password *.
- Date of birth: Day (1-31), Month (January-December), Year (2021 down to 1900) - optional.
- Checkboxes "Sign up for our newsletter!", "Receive special offers from our partners!".
- First name *, Last name *, Company, Address * (Street address, P.O. Box, Company name, etc.), Address 2,
  Country * (India default; India, United States, Canada, Australia, Israel, New Zealand, Singapore), State *, City *, Zipcode *, Mobile Number *.
- Create Account button -> "ACCOUNT CREATED!" page with Continue -> home, "Logged in as <name>" (published case, not walked).
- Delete Account (menu, when logged in) -> "ACCOUNT DELETED!" + Continue (published case, not walked).
All locators: see locators.md.

## Login flow
1. Open `/login`.
2. Fill `[data-qa="login-email"]` with the login's Username (it is the email), `[data-qa="login-password"]` with Password.
3. Click `[data-qa="login-button"]`. Success = "Logged in as" in the top bar; failure = message above.
Trova knows these steps for the login "Test user".

## Roles / logins (Test)
| Login | Fields | What it is |
|---|---|---|
| Test user | Username (= Email Address), Password | Shopper. 2026-11-04: refused - "Your email or password is incorrect!" (account probably not on the site). |
| New Account | Email, Password, Name | Data for a new sign-up (Name, Email Address, Password). |
Only one kind of person: the shopper (visitor before sign-up, member after). No admin screens.

## Quirks
- Google ads/consent frames load on every page; a full-screen ad can open with `#google_vignette` in the URL - reload or go back.
- Odd page texts ("Login portal setup", "You have been successfully subscribed!") flash from ads/footer - ignore them.
- Accounts on this public demo can vanish; create the account in set-up (API createAccount) rather than trusting a saved one.
- The zipcode label has no `for` attribute - use `#zipcode`.

### Test ideas
- [hybrid] Sign up a new shopper with the New Account data on Signup / Login, fill Enter Account Information and Address Information, check "ACCOUNT CREATED!" and "Logged in as", clean-up by API deleteAccount.
- [web] Sign up with an email that already has an account (made by API createAccount) and check "Email Address already exist!"; clean-up by API deleteAccount.
- [web] Leave each required field on the Signup page empty (Password, First name, Last name, Address, State, City, Zipcode, Mobile Number) and check the account is not created.
- [web] Log in with a wrong password on Signup / Login and check "Your email or password is incorrect!".
- [hybrid] Create an account by API, log in on Signup / Login, check "Logged in as <name>", press Delete Account and check "ACCOUNT DELETED!".
- [api] createAccount -> getUserDetailByEmail returns the same name and address -> verifyLogin "User exists!" -> deleteAccount "Account deleted!".
- [api] createAccount twice with the same email and check the second is refused; clean-up deleteAccount.
