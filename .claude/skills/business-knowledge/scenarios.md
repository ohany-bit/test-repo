# End-to-end scenarios - Automation Exercise
| Flow | Who | Steps | Result | Status (2026-11-04) |
|---|---|---|---|---|
| Shopper signs up | Visitor | Signup / Login → Name + Email → Signup → account and address details → Create Account → Continue | Account made, signed in as <name> | not walked (steps up to Create Account seen) |
| Sign-up with a used email | Visitor | Signup / Login → Name + an existing Email → Signup | "Email Address already exist!", stays on Signup / Login | not walked (document) |
| Shopper signs in | Shopper | Signup / Login → Email + Password → Login | "Logged in as <name>" | not walked (Test user refused) |
| Wrong sign-in | Shopper | Signup / Login → wrong Email/Password → Login | "Your email or password is incorrect!" | walked |
| Shopper deletes account | Shopper | signed in → Delete Account → Continue | "ACCOUNT DELETED!", signed out | not walked (document) |
| Shopper signs out | Shopper | signed in → Logout | back on Signup / Login | not walked (document) |
