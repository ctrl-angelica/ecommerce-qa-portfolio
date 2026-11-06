# QA Test Cases

> **Related Test Plan ID:** TP-ECOMQA-001 · **Test case set version:** 0.2 (draft) · **QA owner:** Angelica Soete
> **Application under test:** Practice Software Testing – Toolshop (https://practicesoftwaretesting.com)
> **Status:** Draft. 25 test cases written, none executed yet. All statuses are `Not Run`.

## About this set

- **Format:** the template from section 3 of *QA Test Cases & Execution Records*. IDs follow `TC-[MODULE]-[NNN]`.
- **Module codes:** `AUTH` Login & registration · `CAT` Catalogue, search & product details · `CART` Cart & promotions · `CHK` Checkout, payment & orders.
- **Design techniques:** equivalence partitioning (valid / invalid / empty input classes) and boundary value analysis for forms and quantities.
- **Requirements:** Cases without a requirement say *TBD* and are linked after your exploratory session.
- **Expected results to confirm:** where the exact message or rule on screen is not known yet, the expected result describes the behaviour in general terms and the Notes line says *confirm exact wording/rule in exploratory session*. Update the expected result before executing.
- **Test data:** no passwords are stored here. Use the demo customer account from the shop's public documentation, and a unique email of your own for registration.
- **Execution results** go in the execution log (section 6 of the Records document) and screenshots in `01-manual-testing/evidence`.

## Overview

| ID | Scenario | Priority | Automation |
|---|---|---|---|
| TC-AUTH-001 | Login with valid credentials | P0 | Candidate |
| TC-AUTH-002 | Login with invalid password | P0 | Candidate |
| TC-AUTH-003 | Login with unregistered email | P1 | Candidate |
| TC-AUTH-004 | Login with empty fields | P1 | Candidate |
| TC-AUTH-005 | Login with invalid email format | P2 | Candidate |
| TC-AUTH-006 | Register with valid data | P1 | Candidate |
| TC-AUTH-007 | Register with an already-registered email | P1 | Manual |
| TC-AUTH-008 | Register with required fields empty | P1 | Manual |
| TC-CAT-001 | Product listing shows name and price | P1 | Manual |
| TC-CAT-002 | Pagination moves between listing pages | P2 | Manual |
| TC-CAT-003 | Out-of-stock product is labelled | P1 | Manual |
| TC-CAT-004 | Search with a term that matches products | P1 | Manual |
| TC-CAT-005 | Search with a term that matches nothing | P2 | Manual |
| TC-CAT-006 | Filter the product listing | P2 | Manual |
| TC-CAT-007 | Open a product detail page | P1 | Manual |
| TC-CART-001 | Add a product to the cart | P0 | Candidate |
| TC-CART-002 | Change quantity updates line and cart total | P0 | Manual |
| TC-CART-003 | Remove an item from the cart | P1 | Manual |
| TC-CART-004 | Invalid promotion code is rejected | P2 | Manual |
| TC-CART-005 | Quantity boundary values (0, 1, very large) | P2 | Manual |
| TC-CHK-001 | Complete checkout as a signed-in customer | P0 | Candidate |
| TC-CHK-002 | Checkout with billing address fields empty | P1 | Manual |
| TC-CHK-003 | Payment with invalid payment details | P0 | Manual |
| TC-CHK-004 | Order appears in order history after checkout | P1 | Candidate |
| TC-CHK-005 | Checkout while signed out requires sign-in | P1 | Manual |

---

## Login & registration (AUTH)

### TC-AUTH-001 — Login with valid credentials

| Field | Details |
|---|---|
| Requirement / user story | TBD (login) |
| Module | Login & registration |
| Priority | P0 |
| Test type | Functional |
| Preconditions | User has an existing registered account, is logged out and is on the login page. |
| Test data | The demo customer account shown on the login page / in the shop's public documentation |
| Environment | Google Chrome on Windows |

**Steps and expected results**

| Step | Action | Expected result |
|---:|---|---|
| 1 | Open https://practicesoftwaretesting.com and click "Sign in". | The login page is shown with email and password fields and a login button. |
| 2 | Enter the valid email and password of the demo customer. | The values are accepted in the fields; the password is masked. |
| 3 | Click the login button. | The user is logged in and taken to their account page. No error message is shown. |
| 4 | Look at the page header. | The header shows the user is signed in (the user's name or an account menu instead of "Sign in"). |

**Automation:** Candidate (data-driven login test, valid data set)

**Notes:** Confirm exact landing page and header wording in exploratory session.

**Expected results:** The user is logged in and can see they are signed in. No error is shown.

**Actual results:** [...]
### TC-AUTH-002 — Login with invalid password

| Field | Details |
|---|---|
| Requirement / user story | TBD (login) |
| Module | Login & registration |
| Priority | P0 |
| Test type | Functional (negative) |
| Preconditions | User has a registered account and is logged out, on the login page. |
| Test data | Valid email of the demo customer; password `WrongPass-123` (any value that is not the real password) |
| Environment | Google Chrome on Windows |

**Steps and expected results**

| Step | Action | Expected result |
|---:|---|---|
| 1 | Open the login page. | The login page is shown. |
| 2 | Enter the valid email and the wrong password. | Values are accepted in the fields. |
| 3 | Click the login button. | The user is not logged in and stays on the login page. |
| 4 | Read the message on the page. | An error message is shown saying the credentials are invalid. It does not say which of the two (email or password) was wrong. |

**Automation:** Candidate (data-driven login test, invalid data set)

**Notes:** Confirm exact error wording in exploratory session.

**Expected results:** Login is refused with an error message. The user stays on the login page and is not logged in.

**Actual results:** [...]
### TC-AUTH-003 — Login with unregistered email

| Field | Details |
|---|---|
| Requirement / user story | TBD (login) |
| Module | Login & registration |
| Priority | P1 |
| Test type | Functional (negative) |
| Preconditions | User is logged out, on the login page. |
| Test data | Email `no.such.user.4821@example.com` (not registered); password `SomePass-123` |
| Environment | Google Chrome on Windows |

**Steps and expected results**

| Step | Action | Expected result |
|---:|---|---|
| 1 | Open the login page. | The login page is shown. |
| 2 | Enter the unregistered email and any password. | Values are accepted in the fields. |
| 3 | Click the login button. | The user is not logged in and stays on the login page. |
| 4 | Read the message on the page. | An error message is shown. It does not confirm whether the email exists. |

**Automation:** Candidate (data-driven login test, invalid data set)

**Notes:** Compare the message with TC-AUTH-002: they should not reveal different information. Confirm exact wording in exploratory session.

**Expected results:** Login is refused with an error message that does not reveal whether the email is registered.

**Actual results:** [...]
### TC-AUTH-004 — Login with empty fields

| Field | Details |
|---|---|
| Requirement / user story | TBD (login validation) |
| Module | Login & registration |
| Priority | P1 |
| Test type | Functional (negative, equivalence partitioning: empty input) |
| Preconditions | User is logged out, on the login page. |
| Test data | Variation A: both fields empty. Variation B: email filled, password empty. Variation C: email empty, password filled. |
| Environment | Google Chrome on Windows |

**Steps and expected results**

| Step | Action | Expected result |
|---:|---|---|
| 1 | Open the login page and leave both fields empty. | The login page is shown. |
| 2 | Click the login button (variation A). | The user is not logged in. A message indicates that the required fields must be filled in. |
| 3 | Repeat with variation B, then variation C. | In each case the user is not logged in and the missing field is indicated. |

**Automation:** Candidate (data-driven login test)

**Notes:** Confirm whether validation happens in the browser or after submitting, and its exact wording, in exploratory session.

**Expected results:** Login is refused in every variation, and each missing field is indicated.

**Actual results:** [...]
### TC-AUTH-005 — Login with invalid email format

| Field | Details |
|---|---|
| Requirement / user story | TBD (login validation) |
| Module | Login & registration |
| Priority | P2 |
| Test type | Functional (negative, equivalence partitioning: invalid format) |
| Preconditions | User is logged out, on the login page. |
| Test data | Emails: `plainaddress`, `missing-at.example.com`, `user@`; any password |
| Environment | Google Chrome on Windows |

**Steps and expected results**

| Step | Action | Expected result |
|---:|---|---|
| 1 | Open the login page. | The login page is shown. |
| 2 | Enter `plainaddress` as email and any password, then click login. | The user is not logged in. The email field is flagged as invalid or an error message is shown. |
| 3 | Repeat with the other two email values. | Same result for each value. |

**Automation:** Candidate (data-driven login test)

**Notes:** Confirm exact behaviour in exploratory session.

**Expected results:** Login is refused for every invalid email format, and the email field is flagged.

**Actual results:** [...]
### TC-AUTH-006 — Register with valid data

| Field | Details |
|---|---|
| Requirement / user story | TBD (registration) |
| Module | Login & registration |
| Priority | P1 |
| Test type | Functional |
| Preconditions | User is logged out and is on the registration page (via the "Register your account" link on the login page). |
| Test data | All required fields filled with valid values. Use a unique email of your own (for example `yourname+tc-auth-006@example.com`) and a password that meets the shop's rules (not stored here). |
| Environment | Google Chrome on Windows |

**Steps and expected results**

| Step | Action | Expected result |
|---:|---|---|
| 1 | Open the login page and click the link to register a new account. | The registration form is shown. |
| 2 | Fill in all required fields with valid data. | No validation errors are shown while filling in. |
| 3 | Submit the form. | The registration is accepted and the user is taken to the login page (or is signed in). No error message is shown. |
| 4 | Log in with the new email and password. | Login succeeds (see TC-AUTH-001 for what "success" looks like). |

**Automation:** Candidate (data-driven registration test)

**Notes:** Confirm required fields and password rules in exploratory session, then add boundary cases for them.

**Expected results:** A new account is created and the user can log in with it.

**Actual results:** [...]
### TC-AUTH-007 — Register with an already-registered email

| Field | Details |
|---|---|
| Requirement / user story | TBD (registration) |
| Module | Login & registration |
| Priority | P1 |
| Test type | Functional (negative) |
| Preconditions | User is logged out, on the registration page. The email used for the new registration already exists (for example the demo customer's). |
| Test data | Already-registered email; all other fields valid |
| Environment | Google Chrome on Windows |

**Steps and expected results**

| Step | Action | Expected result |
|---:|---|---|
| 1 | Open the registration page. | The registration form is shown. |
| 2 | Fill in all fields with valid data, using the already-registered email. | No errors while filling in. |
| 3 | Submit the form. | No second account is created. A message says the email is already in use. |

**Automation:** Manual

**Notes:** Confirm exact wording in exploratory session.

**Expected results:** No second account is created. A message says the email is already in use.

**Actual results:** [...]
### TC-AUTH-008 — Register with required fields empty

| Field | Details |
|---|---|
| Requirement / user story | TBD (registration validation) |
| Module | Login & registration |
| Priority | P1 |
| Test type | Functional (negative, equivalence partitioning: empty input) |
| Preconditions | User is logged out, on the registration page. |
| Test data | Variation A: all fields empty. Variation B: all valid except one required field empty (repeat for each required field). |
| Environment | Google Chrome on Windows |

**Steps and expected results**

| Step | Action | Expected result |
|---:|---|---|
| 1 | Open the registration page and submit the empty form (variation A). | The account is not created. Each missing required field is flagged. |
| 2 | Fill all fields except one required field and submit (variation B). | The account is not created. The empty field is flagged. |
| 3 | Repeat step 2 for each remaining required field. | Same result for each field. |

**Automation:** Manual

**Notes:** List the required fields from the form in the evidence. Confirm exact wording in exploratory session.

**Expected results:** No account is created, and each missing required field is flagged.

**Actual results:** [...]

---

## Catalogue, search & product details (CAT)
### TC-CAT-001 — Product listing shows name and price

| Field | Details |
|---|---|
| Requirement / user story | REQ-001 |
| Module | Catalogue, search & product details |
| Priority | P1 |
| Test type | Functional |
| Preconditions | None. Signed in or out. |
| Test data | None |
| Environment | Google Chrome on Windows |

**Steps and expected results**

| Step | Action | Expected result |
|---:|---|---|
| 1 | Open https://practicesoftwaretesting.com. | The home page loads with a product listing. |
| 2 | Look at every product card on the first page. | Each product shows a name and a price. No product is missing either. |

**Automation:** Manual

**Notes:** Record how many products are shown on the page.

**Expected results:** Every product in the listing shows a name and a price.

**Actual results:** [...]
### TC-CAT-002 — Pagination moves between listing pages

| Field | Details |
|---|---|
| Requirement / user story | REQ-002 |
| Module | Catalogue, search & product details |
| Priority | P2 |
| Test type | Functional |
| Preconditions | The home page product listing is open. |
| Test data | None |
| Environment | Google Chrome on Windows |

**Steps and expected results**

| Step | Action | Expected result |
|---:|---|---|
| 1 | Scroll to the pagination controls under the listing. | Page numbers (5 pages observed on 2026-11-06) and a way to go to the next page are shown. |
| 2 | Click page 2. | A different set of products is shown. Page 2 is marked as the current page. |
| 3 | Click the last page, then the first page. | Each page shows products; no product is shown on two different pages. |

**Automation:** Manual

**Notes:** Number of pages may change if the shop's data changes; record the count on the day.

**Expected results:** Each listing page shows different products and the current page is marked.

**Actual results:** [...]
### TC-CAT-003 — Out-of-stock product is labelled

| Field | Details |
|---|---|
| Requirement / user story | REQ-003 |
| Module | Catalogue, search & product details |
| Priority | P1 |
| Test type | Functional |
| Preconditions | An out-of-stock product exists in the listing (observed on 2026-11-06: "Long Nose Pliers"). |
| Test data | Product "Long Nose Pliers" (or any product labelled out of stock on the day) |
| Environment | Google Chrome on Windows |

**Steps and expected results**

| Step | Action | Expected result |
|---:|---|---|
| 1 | Find the out-of-stock product in the listing. | The product card shows an out-of-stock label. |
| 2 | Open the product's detail page. | The detail page also indicates the product is out of stock. |
| 3 | Look for the add-to-cart button. | The product cannot be added to the cart (button disabled or absent). |

**Automation:** Manual

**Notes:** The label was shown in Dutch because of the browser language; set Chrome to English and record both. Confirm step 2 and 3 behaviour in exploratory session.

**Expected results:** The out-of-stock product is labelled as such and cannot be added to the cart.

**Actual results:** [...]
### TC-CAT-004 — Search with a term that matches products

| Field | Details |
|---|---|
| Requirement / user story | TBD (search) |
| Module | Catalogue, search & product details |
| Priority | P1 |
| Test type | Functional |
| Preconditions | Home page is open. |
| Test data | Search term `hammer` (or a product name visible in the listing) |
| Environment | Google Chrome on Windows |

**Steps and expected results**

| Step | Action | Expected result |
|---:|---|---|
| 1 | Type the search term in the search box. | The term appears in the box. |
| 2 | Submit the search (Enter or the search button). | A result list is shown. |
| 3 | Check each result. | Every result is related to the search term (name matches). Each result shows a name and a price. |

**Automation:** Manual

**Notes:** Also try upper-case (`HAMMER`) and a partial term (`ham`) as variations. Confirm matching rule in exploratory session.

**Expected results:** Only products related to the search term are shown, each with a name and a price.

**Actual results:** [...]
### TC-CAT-005 — Search with a term that matches nothing

| Field | Details |
|---|---|
| Requirement / user story | TBD (search) |
| Module | Catalogue, search & product details |
| Priority | P2 |
| Test type | Functional (negative) |
| Preconditions | Home page is open. |
| Test data | Search term `zzzxqwv` |
| Environment | Google Chrome on Windows |

**Steps and expected results**

| Step | Action | Expected result |
|---:|---|---|
| 1 | Type the search term in the search box and submit. | The search is processed without an error page. |
| 2 | Look at the result area. | A "no results" message is shown instead of products. |

**Automation:** Manual

**Notes:** Variation: submit an empty search and note the behaviour. Confirm wording in exploratory session.

**Expected results:** A "no results" message is shown and no products are listed. There is no error page.

**Actual results:** [...]
### TC-CAT-006 — Filter the product listing

| Field | Details |
|---|---|
| Requirement / user story | REQ-004 |
| Module | Catalogue, search & product details |
| Priority | P2 |
| Test type | Functional |
| Preconditions | Home page product listing is open. |
| Test data | One filter option of your choice (for example a category), chosen after the exploratory session |
| Environment | Google Chrome on Windows |

**Steps and expected results**

| Step | Action | Expected result |
|---:|---|---|
| 1 | Locate the filter control on the listing. | A filter control with options is shown. |
| 2 | Select one filter option. | The listing updates and shows only products that belong to the selected option. |
| 3 | Clear the filter. | The full listing is shown again. |

**Automation:** Manual

**Notes:** Filter options are not yet explored (REQ-004). Name the exact filter option in Test data once known, and consider one case per filter type.

**Expected results:** Only products that match the selected filter are shown. Clearing the filter shows the full listing again.

**Actual results:** [...]
### TC-CAT-007 — Open a product detail page

| Field | Details |
|---|---|
| Requirement / user story | TBD (product details) |
| Module | Catalogue, search & product details |
| Priority | P1 |
| Test type | Functional |
| Preconditions | Home page product listing is open. |
| Test data | Any in-stock product |
| Environment | Google Chrome on Windows |

**Steps and expected results**

| Step | Action | Expected result |
|---:|---|---|
| 1 | Click an in-stock product in the listing. | The product detail page opens. |
| 2 | Compare the name and price with the listing. | Name and price are the same as on the listing. |
| 3 | Check the rest of the page. | An image, a description, and an add-to-cart control are shown. |

**Automation:** Manual

**Notes:** Record the product name and price in the evidence.

**Expected results:** The detail page shows the same name and price as the listing, plus an image, a description and an add-to-cart control.

**Actual results:** [...]

---

## Cart & promotions (CART)
### TC-CART-001 — Add a product to the cart

| Field | Details |
|---|---|
| Requirement / user story | TBD (cart) |
| Module | Cart & promotions |
| Priority | P0 |
| Test type | Functional |
| Preconditions | Empty cart. Signed in or out. |
| Test data | Any in-stock product, quantity 1 |
| Environment | Google Chrome on Windows |

**Steps and expected results**

| Step | Action | Expected result |
|---:|---|---|
| 1 | Open an in-stock product's detail page. | The detail page is shown. |
| 2 | Click add to cart. | A confirmation is shown and the cart icon shows 1 item. |
| 3 | Open the cart. | The cart contains the product with quantity 1 and the correct unit price. |

**Automation:** Candidate (part of the end-to-end flow)

**Notes:** Record the product name and price for comparison in TC-CART-002.

**Expected results:** The product is in the cart with quantity 1 and the correct unit price.

**Actual results:** [...]
### TC-CART-002 — Change quantity updates line and cart total

| Field | Details |
|---|---|
| Requirement / user story | TBD (cart totals) |
| Module | Cart & promotions |
| Priority | P0 |
| Test type | Functional |
| Preconditions | Cart contains one in-stock product, quantity 1. |
| Test data | Quantity 3 |
| Environment | Google Chrome on Windows |

**Steps and expected results**

| Step | Action | Expected result |
|---:|---|---|
| 1 | Open the cart and note the unit price, line total and cart total. | Line total and cart total equal the unit price for quantity 1. |
| 2 | Change the quantity to 3. | The quantity shows 3. |
| 3 | Check the totals. | The line total equals unit price × 3. The cart total is updated accordingly (including any rules the shop applies, such as tax or discounts). |

**Automation:** Manual

**Notes:** Calculate the expected total by hand and write it in the evidence. Confirm how the cart total is built (tax, shipping) in exploratory session.

**Expected results:** The line total and the cart total are correct for the new quantity.

**Actual results:** [...]
### TC-CART-003 — Remove an item from the cart

| Field | Details |
|---|---|
| Requirement / user story | TBD (cart) |
| Module | Cart & promotions |
| Priority | P1 |
| Test type | Functional |
| Preconditions | Cart contains two different in-stock products. |
| Test data | Two different products |
| Environment | Google Chrome on Windows |

**Steps and expected results**

| Step | Action | Expected result |
|---:|---|---|
| 1 | Open the cart. | Both products are listed. |
| 2 | Remove the first product. | Only the second product remains. Cart total and item count are updated. |
| 3 | Remove the second product. | The cart is empty and an empty-cart state is shown. |

**Automation:** Manual

**Notes:** None.

**Expected results:** Removed items are gone and the totals are updated. Removing every item leaves an empty cart.

**Actual results:** [...]
### TC-CART-004 — Invalid promotion code is rejected

| Field | Details |
|---|---|
| Requirement / user story | TBD (promotions) |
| Module | Cart & promotions |
| Priority | P2 |
| Test type | Functional (negative) |
| Preconditions | Cart contains one in-stock product. A promotion-code field is available in the cart. |
| Test data | Code `NOTACODE123` |
| Environment | Google Chrome on Windows |

**Steps and expected results**

| Step | Action | Expected result |
|---:|---|---|
| 1 | Open the cart and note the cart total. | Cart total is shown. |
| 2 | Enter the invalid code and apply it. | The code is rejected with a message. |
| 3 | Check the cart total. | The cart total is unchanged. |

**Automation:** Manual

**Notes:** Only run if the cart has a promotion-code field; otherwise mark `Not Applicable` with a reason. If a valid code exists, add a separate case for it after the exploratory session.

**Expected results:** The invalid code is rejected with a message and the cart total does not change.

**Actual results:** [...]
### TC-CART-005 — Quantity boundary values (0, 1, very large)

| Field | Details |
|---|---|
| Requirement / user story | TBD (cart quantity) |
| Module | Cart & promotions |
| Priority | P2 |
| Test type | Functional (boundary value analysis) |
| Preconditions | Cart contains one in-stock product. |
| Test data | Quantities: `0`, `1`, `99999` |
| Environment | Google Chrome on Windows |

**Steps and expected results**

| Step | Action | Expected result |
|---:|---|---|
| 1 | Set the quantity to `1`. | Quantity 1 is accepted and totals are correct. |
| 2 | Set the quantity to `0`. | Quantity 0 is not accepted as a valid order: the item is removed or the value is rejected. The cart does not show a zero or negative total. |
| 3 | Set the quantity to `99999`. | The shop either accepts it with correct totals or rejects it with a message. No error page or incorrect total is shown. |

**Automation:** Manual

**Notes:** Confirm the shop's quantity rule in exploratory session, then add the exact upper boundary as a test value.

**Expected results:** Quantity 1 gives correct totals, quantity 0 is not accepted as an order, and a very large quantity is handled without an error or a wrong total.

**Actual results:** [...]

---

## Checkout, payment & orders (CHK)
### TC-CHK-001 — Complete checkout as a signed-in customer

| Field | Details |
|---|---|
| Requirement / user story | TBD (checkout) |
| Module | Checkout, payment & orders |
| Priority | P0 |
| Test type | Functional (end-to-end) |
| Preconditions | Logged in as the demo customer. Cart contains one in-stock product. |
| Test data | Demo customer account; billing address with valid test values; a valid payment method available on the shop (use test/fake payment data only, never real card data) |
| Environment | Google Chrome on Windows |

**Steps and expected results**

| Step | Action | Expected result |
|---:|---|---|
| 1 | Open the cart and click proceed to checkout. | The checkout opens with the correct product and total. |
| 2 | Fill in the billing address with valid data and continue. | The address is accepted and the payment step is shown. |
| 3 | Choose a payment method and enter valid test payment data. | The payment details are accepted. |
| 4 | Confirm the order. | An order confirmation is shown, with an order number or confirmation message. |
| 5 | Check the cart. | The cart is empty. |

**Automation:** Candidate (end-to-end Playwright flow: log in, find a product, add to cart, check out, confirmation)

**Notes:** Confirm payment methods and test data accepted by the shop in exploratory session.

**Expected results:** The order is placed, a confirmation is shown and the cart is empty afterwards.

**Actual results:** [...]
### TC-CHK-002 — Checkout with billing address fields empty

| Field | Details |
|---|---|
| Requirement / user story | TBD (checkout validation) |
| Module | Checkout, payment & orders |
| Priority | P1 |
| Test type | Functional (negative, equivalence partitioning: empty input) |
| Preconditions | Logged in as the demo customer. Cart contains one in-stock product. User is on the billing address step. |
| Test data | Variation A: all required fields empty. Variation B: all valid except one required field empty. |
| Environment | Google Chrome on Windows |

**Steps and expected results**

| Step | Action | Expected result |
|---:|---|---|
| 1 | On the billing address step, leave all required fields empty and try to continue (variation A). | The user cannot continue. Each missing required field is flagged. |
| 2 | Fill all fields except one required field and try to continue (variation B). | The user cannot continue. The empty field is flagged. |

**Automation:** Manual

**Notes:** The demo account may have an address pre-filled: clear it first. Confirm required fields in exploratory session.

**Expected results:** The user cannot continue past the billing address step, and each missing field is flagged.

**Actual results:** [...]
### TC-CHK-003 — Payment with invalid payment details

| Field | Details |
|---|---|
| Requirement / user story | TBD (payment) |
| Module | Checkout, payment & orders |
| Priority | P0 |
| Test type | Functional (negative) |
| Preconditions | Logged in as the demo customer. Cart contains one in-stock product. User is on the payment step with a method that needs payment details. |
| Test data | Clearly invalid test values (for example a too-short card number, or an expiry date in the past). Never use real card data. |
| Environment | Google Chrome on Windows |

**Steps and expected results**

| Step | Action | Expected result |
|---:|---|---|
| 1 | On the payment step, enter invalid payment details. | The invalid fields are flagged or the form shows a message. |
| 2 | Try to confirm the order. | The order is not placed. The user stays on the payment step with a clear message. |
| 3 | Check the order history. | No new order was created. |

**Automation:** Manual

**Notes:** Confirm which payment methods validate their data in exploratory session; pick one and name it in Test data.

**Expected results:** The order is not placed, the user is told the payment details are invalid, and no order is created.

**Actual results:** [...]
### TC-CHK-004 — Order appears in order history after checkout

| Field | Details |
|---|---|
| Requirement / user story | TBD (orders) |
| Module | Checkout, payment & orders |
| Priority | P1 |
| Test type | Functional |
| Preconditions | TC-CHK-001 has passed and the order number is known. Logged in as the same user. |
| Test data | Order from TC-CHK-001 |
| Environment | Google Chrome on Windows |

**Steps and expected results**

| Step | Action | Expected result |
|---:|---|---|
| 1 | Open the page that lists the user's orders / invoices. | A list of orders is shown. |
| 2 | Find the order from TC-CHK-001. | The order is in the list with the same order number. |
| 3 | Open the order. | The order shows the correct product(s), quantity and total. |

**Automation:** Candidate (API-assisted setup, then UI check)

**Notes:** Viewing orders only: account management itself is out of scope. Confirm where the order list is located in exploratory session.

**Expected results:** The order from TC-CHK-001 is in the order list with the correct product, quantity and total.

**Actual results:** [...]
### TC-CHK-005 — Checkout while signed out requires sign-in

| Field | Details |
|---|---|
| Requirement / user story | TBD (checkout access) |
| Module | Checkout, payment & orders |
| Priority | P1 |
| Test type | Functional |
| Preconditions | User is logged out. Cart contains one in-stock product. |
| Test data | None |
| Environment | Google Chrome on Windows |

**Steps and expected results**

| Step | Action | Expected result |
|---:|---|---|
| 1 | Open the cart and click proceed to checkout. | The user is asked to sign in or register before continuing (or can continue as a guest, if the shop allows it). |
| 2 | Sign in with the demo customer. | The user continues to checkout with the cart still containing the product. |

**Automation:** Manual

**Notes:** Expected result depends on whether the shop supports guest checkout. Confirm in exploratory session and rewrite the expected result.

**Expected results:** A signed-out user must sign in (or can continue as a guest, if the shop allows it) and the cart still contains the product.

**Actual results:** [...]

---

## Change history

| Version | Date | Author | Change |
|---|---|---|---|
| 0.2 | 2026-11-06 | Angelica Soete | 25 test cases drafted from the Test Cases & Execution Records template |
