---
name: api-catalog
description: The Automation Exercise API (automationexercise.com/api) - account calls for set-up and clean-up of sign-up tests. Read before calling the API.
---

# Automation Exercise API
Source: the app's own "API Testing" page `/api_list` (2026-11-04). 🔎 = read from the app, not verified by a call.
Base: https://automationexercise.com/api/ · bodies are form fields (multipart / x-www-form-urlencoded), answers are JSON
`{"responseCode": <n>, "message": "..."}` - the HTTP status may stay 200, check `responseCode`.

## Account (sign-up part)
| | Method | Path | Body | For | Answer |
|---|---|---|---|---|---|
| 🔎 | POST | /api/createAccount | name, email, password, title (Mr/Mrs/Miss), birth_date, birth_month, birth_year, firstname, lastname, company, address1, address2, country, zipcode, state, city, mobile_number | set-up: make a shopper | 201 "User created!" |
| 🔎 | DELETE | /api/deleteAccount | email, password | clean-up: remove the shopper | 200 "Account deleted!" |
| 🔎 | PUT | /api/updateAccount | same as createAccount | change a shopper | 200 "User updated!" |
| 🔎 | GET | /api/getUserDetailByEmail?email= | - | read a shopper's details | 200 user detail JSON |
| 🔎 | POST | /api/verifyLogin | email, password | check a login | 200 "User exists!" / 404 "User not found!" / 400 missing parameter |
| 🔎 | DELETE | /api/verifyLogin | - | negative | 405 "This request method is not supported." |

Other groups on /api_list (not in this part): productsList, brandsList, searchProduct.

## Pages and calls
- Signup / Login and Signup pages call no API: they are full form posts to `/login` and `/signup` (with a CSRF field),
  then the account is made on Create Account. Only ad/analytics calls show in the network.

## Recipes
- Set-up shopper: POST createAccount with the New Account login's Name, Email, Password + address fields.
- Clean-up: DELETE deleteAccount with the same email and password (also after a sign-up done in the app).
