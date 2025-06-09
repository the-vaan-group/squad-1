# Pull Requests

For ideal collaboration between team members, the aim is to follow industry best practices for
PRs. This document outlines some of those practices and expectations.

## Table of Contents

1. [Branch Naming Convention](#-branch-naming-convention)
2. [Draft PRs](#-draft-prs)
3. [Pull Request Title Guidelines](#-pull-request-title-guidelines)
4. [Pull Request Descriptions](#-pr-descriptions)
5. [Reviewing Pull Requests](#-reviewing-pull-requests)

---

## 🗂️ Branch Naming Convention

All branches must include the corresponding ticket number for traceability. Use the following format:

`<type>/<ticket-number>-short-description`

---

### 🔧 Types

- `feature/` — For new features  
  _Example_: `feature/HEX-1234-add-product-carousel`

- `hotfix/` — For urgent fixes on production  
  _Example_: `hotfix/HEX-5678-fix-header-overlap`

- `bug/` — For bug fixes that are not urgent hotfixes  
  _Example_: `bug/HEX-4321-fix-login-error`

- `chore/` — For maintenance tasks, refactoring, or build-related updates  
  _Example_: `chore/HEX-2468-upgrade-dependencies`

- `doc/` — For documentation updates  
  _Example_: `doc/HEX-1357-update-readme`

---

### ✅ Tips

- Use lowercase letters and hyphens (`-`) to separate words in the description.
- If no ticket is available, use `no-ticket` instead of a ticket number.  
  _Example_: `chore/no-ticket-update-eslint-config`

---

## 🗒️ Draft PRs

We should make a draft PR at the end of our day or as we approach a ticket's
estimated time, whichever comes first. This allows us to encapsulate the
direction we are looking to head by leveraging the conversation from the
implementation meeting, as well as giving others additional insight into the approach.

This also is a public indication of what is being worked on and the effort towards it and allows another team member to easily pickup work when needed.

The PR can be marked as a draft in Github until we are ready for final review by a team member. Once that review is required, make sure to add the team members from the squad to the PR so they can be notified a review is needed from them.

## 📄 Pull Request Title Guidelines

To ensure our GitHub pull request list is easy to scan and understand, **all PR titles must follow a consistent format**. This helps with tracking work, improving collaboration, and simplifying releases.

---

## ✅ Standard Format

### For ticketed work:

`[HEX-1234] Brief, clear description of the change`

- `HEX-1234` should match the ticket number in our issue tracker (e.g., Jira, Linear).
- Keep the description short but specific.
- Use sentence case: capitalize only the first word and proper nouns.

**Example:**
`[HEX-4521] Add pagination to project dashboard`

---

### For unticketed work:

`[NO-TICKET] Brief, clear description of the change`

- Use only when no ticket exists and one isn't needed (e.g., minor CI fix, internal tooling).
- These PRs should be rare and must include a short explanation in the PR body.

**Example:**
`[NO-TICKET] Fix broken GitHub Actions workflow for staging deploy`

---

### For work that has been hotfixed:

`[HOTFIX] [HEX-4521] Brief, clear description of the change`

- Use only when the work in the PR has been hotfixed on any live store theme.
- If there is no task ID, you may omit it.

**Example:**
`[HOTFIX] Fix convert script on US store`

---

### ❌ What Not to Do

- Do **not** omit the ticket or use free-form titles like `Fix bug` or `Update things`.
- Do **not** use placeholders like `[HEX-000]` — see rationale below.
- Do **not** use inconsistent casing like `[hex-1234]` or `[Hex1234]`.

---

### 💡 Tips

- Keep titles under 60 characters if possible.
- If a PR involves multiple unrelated concerns, consider splitting it.
- A good title saves reviewers time and helps with release notes and audits.

---

### 📌 Why Use `[NO-TICKET]` Instead of `[HEX-000]`?

Using `[NO-TICKET]` is intentional and preferred for clarity and maintainability.

| Format        | Clarity | Risk of Confusion | Good for Automation | Recommended |
| ------------- | ------- | ----------------- | ------------------- | ----------- |
| `[HEX-000]`   | Low     | High              | Medium              | ❌ No       |
| `[NO-TICKET]` | High    | Low               | High                | ✅ Yes      |

#### Benefits of `[NO-TICKET]`:

- **Explicitly communicates** there's no associated ticket.
- Avoids **confusion or collisions** with real ticket numbers.
- Easier to **search and filter** in GitHub or with tooling.
- Promotes better **accountability** and encourages proper tracking.
- Works well with **automated changelogs** or internal CI/CD scripts.

## 📄 PR Descriptions

Here at Vaan, we have a template for PR descriptions as part of every project.
Filling out this information helps the reviewer to understand the context of
what you are working on as well as providing a quick snapshot of the changes
being made. It lives with the git history and can be quickly cross-referenced.

It should have enough context for why, what changed as part of this
implementation, and how to test. It should also include any deploy
information necessary.

**Your Goal**
To create a robust enough description for your Reviewer to have all relevant
information needed to review your code.

### 🏷️ Ticket

This is a place to link the ticket. It is recommended to copy the ticket number and
title and hyperlink it as part of the PR.

---

### 📝 Description

Should provide a quick synopsis of why we are making this change. If it makes
sense to copy the user story or some of the description from the ticket, then
feel free to do so.

---

### 📎 Changes

This should include an overview of the changes you have made to the code base as
well as any additional net new information that should be included as part of
this feature (e.g. metaobjects, metafields, new settings, etc)

See [merging tasks](merging-tasks.md) for more information on changes that need to be included in this section.

---

### 🖍️ Testing

Any information necessary for the Reviewer to test your code should be included
here. See the section below on [Reviewing Pull
Requests](#-reviewing-pull-requests) for the expectations of a reviewer. Some
examples of helpful information might be the figma, preview
them, or a specific preview theme's customizer URL.

While most of this information is optional, outside of hotfixes, **every PR
should include a link to a preview theme for easy testing**.

## 👓 Reviewing Pull Requests

As an engineer, **you are a reviewer first** and a creator second. We have
agreed upon squad expectations for reviewers based on this premise.

### ❓ Reviewing Priority

Reviewing PRs is a key way we work as a team to ensure the features being released maintain consistency, quality of approach, and work in general. Unblocking other's work is a top priority for each team member and as such, PR reviews are a top priority for each of us.
A review shouldn't include large overhauls of an implementation unless
absolutely necessary. It should be about refinements, small improvements, and
best practices. We should be discussing the steps for implementation in the
original implementation post not in the PR review. This is also an additional
benefit to draft PRs as some comments can be made as a PR is in progress rather
than final completion.

---

### 📍 Expectations of reviewers

As a reviewer, you take equal ownership of the code and feature being released to ensure it is working as expected through the happy path, utilizes Vaan coding patterns, implements as planned in the implementation meeting, and meets the basic acceptance criteria.

A key part of performing a PR review is opening up the preview theme, and running through the test criteria. If there isn't test criteria and enough context in the PR for you to feel confident in testing the work, you should request more information. If a feature gets released or sent to QA and there is a significant part of the AC missing or there is a clear error, the expectation is it should have to be caught as part of a PR review and a conversation will likely happen between all members as to why that was missed.

Reviews are not QA and do not need to check for every edge case nor test that it works on all browsers or devices or attempt to break the feature.
