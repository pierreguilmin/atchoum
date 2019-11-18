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
  - which optimization algorithm to use
  - the number `l` of wishes per person
  - ...
- Forms can be shared to participants in easy and various ways.
- Web-app.

### Role-based access control (roles and permissions)
Three different roles described underneath: **administrator** (later called *admin*), **support** and **participant**.

|                                     | Admin              | Support            | Participant |
| ----------------------------------- | :----------------: | :----------------: | :---------: |
| Form creation                       | :white_check_mark: |                    |             |
| Form parameters                     | :white_check_mark: |                    |             |
| Form modification                   | :white_check_mark: | :question:         |             |
| Form closing                        | :white_check_mark: | :question:         |             |
| Share the form to a given email     | :white_check_mark: | :white_check_mark: |             |
| Form results by participant - live* | :white_check_mark: | :white_check_mark: |             |
| Form results by participant         | :white_check_mark: | :white_check_mark: | :question:  |

:white_check_mark: : can do  
:question: : admin dependent  
*\* live means that the form has not yet been closed by the admin*

### Form sharing options
How does an admin or a support share the form to participants ?
- Issue with a link: how do you uniquely identify someone who uses the link to access the form?
- Send an email to a list of email adresses.

### Additional functionalities
- Categories description or even caterogies name can have images, formated text, ...
- Statistics after the repartition (worst selected wich number, mean selected wich number, ...).
- Notifications (ex: when the form opens, 1 day before the form ends, when the results are available, ...) → configurable by the admin.

## Design
Interactive and innovative design. Simple, light, straightforward (like [WeTransfer](https://wetransfer.com/) or [Google Forms](https://docs.google.com/forms/)).
