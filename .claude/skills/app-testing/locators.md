# Locators - Automation Exercise (Test)
Checked 2026-11-04 in the browser: one match each. UI language: English only.

| Page | Element | Locator | Text (EN) | Checked |
|---|---|---|---|---|
| any | Menu Signup / Login | `//a[@href='/login']` | Signup / Login | yes |
| /login | Login title | `//h2[normalize-space()='Login to your account']` | Login to your account | yes |
| /login | Login email | `[data-qa="login-email"]` | Email Address | yes |
| /login | Login password | `[data-qa="login-password"]` | Password | yes |
| /login | Login button | `[data-qa="login-button"]` | Login | yes |
| /login | Login error | `//p[normalize-space()='Your email or password is incorrect!']` | Your email or password is incorrect! | yes |
| /login | Signup title | `//h2[normalize-space()='New User Signup!']` | New User Signup! | yes |
| /login | Signup name | `[data-qa="signup-name"]` | Name | yes |
| /login | Signup email | `[data-qa="signup-email"]` | Email Address | yes |
| /login | Signup button | `[data-qa="signup-button"]` | Signup | yes |
| /login | Email exists error | `//p[normalize-space()='Email Address already exist!']` | Email Address already exist! | no (not shown - published case) |
| /signup | Title Mr. | `#id_gender1` | Mr. | yes |
| /signup | Title Mrs. | `#id_gender2` | Mrs. | yes |
| /signup | Name | `[data-qa="name"]` (#name) | Name * | yes |
| /signup | Email (disabled) | `[data-qa="email"]` (#email) | Email * | yes |
| /signup | Password | `[data-qa="password"]` (#password) | Password * | yes |
| /signup | Birth day | `[data-qa="days"]` (#days) | Day | yes |
| /signup | Birth month | `[data-qa="months"]` (#months) | Month | yes |
| /signup | Birth year | `[data-qa="years"]` (#years) | Year | yes |
| /signup | Newsletter | `#newsletter` | Sign up for our newsletter! | yes |
| /signup | Partner offers | `#optin` | Receive special offers from our partners! | yes |
| /signup | First name | `[data-qa="first_name"]` | First name * | yes |
| /signup | Last name | `[data-qa="last_name"]` | Last name * | yes |
| /signup | Company | `[data-qa="company"]` | Company | yes |
| /signup | Address | `[data-qa="address"]` (#address1) | Address * | yes |
| /signup | Address 2 | `[data-qa="address2"]` | Address 2 | yes |
| /signup | Country | `[data-qa="country"]` | Country * | yes |
| /signup | State | `[data-qa="state"]` | State * | yes |
| /signup | City | `[data-qa="city"]` | City * | yes |
| /signup | Zipcode | `[data-qa="zipcode"]` | Zipcode * | yes |
| /signup | Mobile Number | `[data-qa="mobile_number"]` | Mobile Number * | yes |
| /signup | Create Account | `[data-qa="create-account"]` | Create Account | yes |
| /account_created | Created title | `[data-qa="account-created"]` | ACCOUNT CREATED! | no (not walked) |
| /account_created | Continue | `[data-qa="continue-button"]` | Continue | no (not walked) |
| any (logged in) | Logged in as | `//a[contains(normalize-space(),'Logged in as')]` | Logged in as <name> | no (login refused) |
| any (logged in) | Delete Account | `//a[@href='/delete_account']` | Delete Account | no (login refused) |
| any (logged in) | Logout | `//a[@href='/logout']` | Logout | no (login refused) |
