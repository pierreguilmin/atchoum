# Specifications

:construction: Work in progress...

This document gathers the high-level specifications for `atchoum` `v1.0`.

:point_up: This document should be updated throughout the project evolution.

> “ We are our choices. ”, Jean-Paul Sartre

## Core functionalities
### Goal
The goal is to ease the creation and the use of **ordered wishes repartition forms** (later called *forms*).

Such forms are used when one needs `n` persons to be assigned to `k` categories (one unique category per person), knowing that each person has some preferences for some categories (such preferred categories are called *wishes*). The usual way of solving this problem is to ask each person to give an ordered list of their `l` wishes (`l ≤ k`), with wish `1` being the category they want the most. Then an optimization algorithm runs to do the repartition, trying to maximize the global satisfaction.

### Core specifications
- Form parameters:
  - the `k` categories name
  - the number `l` of wishes per person
  - the integer vector `v` defining the maximum number of persons accepted for each category
  - which optimization algorithm to use
  - ...
- Forms can be shared to participants in easy and various ways (see the [Form sharing options](#form-sharing-options) section).
- Web-app.
- Anyone can create forms and share them, but they need an account on the website to do so.

### Role-based access control (roles and permissions)
Three different roles described underneath: **administrator** (later called *admin*), **support** and **participant**.

|                                      | Admin              | Support            | Participant |
| ------------------------------------ | :----------------: | :----------------: | :---------: |
| Form creation                        | :white_check_mark: |                    |             |
| Form parameters                      | :white_check_mark: |                    |             |
| Change user role*                    | :white_check_mark: |                    |             |
| Form sharing mode                    | :white_check_mark: |                    |             |
| Form modification                    | :white_check_mark: | :question:         |             |
| Form closing                         | :white_check_mark: | :question:         |             |
| Share the form to a given email      | :white_check_mark: | :white_check_mark: |             |
| Form results by participant - live** | :white_check_mark: | :white_check_mark: |             |
| Form results by participant          | :white_check_mark: | :white_check_mark: | :question:  |

:white_check_mark: : can do  
:question: : admin dependent  
*\* for example, a support can become an admin (so we can have multiple admins for a single form)*  
*\*\* live means that the form has not yet been closed by the admin*

### Accounts
Every admin needs to have an account on the website.  
Supports and participants don't need to create an account.

### Form sharing
How does an admin or a support share the form to participants ? We distinguish two use case.

**:lock: Secure - via a list of email adresses** Any admin or support share the form to a list of email adresses. Each participant receives a personal tokened url by email, allowing him to fill the form under his identity.

**:unlock: Unsecure - via a global sharing link** A global sharink link can be shared to anyone. When a new participant accesses the form, he has to give his email adress before submitting the form. He then receives an email with a personal tokened url. If a participant gives an already used email adress, he can't submit the form.  
:warning: A global sharing link may cause two problems. First, unknown participants can fill the form. Second, someone can fill the form using someone's else email adress, giving that this person didn't fill the form yet.

:information_source: For both use case, the personal url can be used by the participant to view and modify his wishes list, after the form has been submitted for the first time.

## Additional functionalities
- Categories description or even caterogies name can have images, formated text, ...
- Statistics after the repartition (worst selected wish number, mean selected wish number, ...).
- Notifications (ex: when the form opens, 1 day before the form ends, when the results are available, ...) → configurable by the admin.
- Propose a QR Code along with the link for the unsecure sharing use case.

## Design
Interactive and innovative design. Simple, light, straightforward (like [WeTransfer](https://wetransfer.com/) or [Google Forms](https://docs.google.com/forms/)).
