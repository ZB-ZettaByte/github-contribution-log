# Contribution 1: Mobile image caption alt text not displayed on desktop and web clients

* **Contribution Number:** 1
* **Student:** Sai Rithwik Kukunuri
* **Issue:** Rocket.Chat Issue #40730
* **Fork:** https://github.com/ZB-ZettaByte/Rocket.Chat
* **Working Branch:** https://github.com/ZB-ZettaByte/Rocket.Chat/tree/fix-issue-40730
* **Status:** Phase III Complete

---

## Why I Chose This Issue

I chose this issue because it is a clear user-facing bug in Rocket.Chat’s desktop and web client. When users send an image with a caption from the mobile app, the caption should still be visible when the message is viewed from desktop or web. Fixing this improves consistency across Rocket.Chat clients and makes image messages easier to understand.

This issue also matches my skills and learning goals because Rocket.Chat is a large TypeScript-based open-source project, and the bug is related to frontend message and image attachment rendering. I wanted to learn how a production chat platform handles attachments across mobile and web clients while practicing the full open-source contribution workflow.

---

## Understanding the Issue

### Problem Description

When a user sends an image with a caption from the Rocket.Chat mobile app, the caption text is not visibly displayed in the desktop and web client. According to the issue and my reproduction, the caption appears to be available through the image attachment metadata or `alt` text, but the web client does not render that value as normal visible caption text.

### Expected Behavior

The caption text should be visible in the desktop and web client when viewing an image that was sent with a caption from the mobile app. The caption should appear near the image in a readable way while still preserving the image `alt` text for accessibility.

### Current Behavior

The image appears in the desktop and web client, but the caption text is missing from the visible message UI. The caption is only available indirectly through the image metadata or `alt` attribute instead of being shown as readable message content.

### Affected Components

The affected area is Rocket.Chat’s web client message rendering flow, especially the components responsible for displaying file and image attachments inside messages.

---

## Reproduction Process

### Environment Setup

I set up the Rocket.Chat development environment and created a working branch in my fork.

**Working branch:**
https://github.com/ZB-ZettaByte/Rocket.Chat/tree/fix-issue-40730

Setup notes:

* Cloned my fork of Rocket.Chat.
* Installed the required project dependencies based on Rocket.Chat setup instructions.
* Started the development server locally.
* Verified that Rocket.Chat was accessible in the browser.
* Created or used a test workspace to reproduce the issue.

### Steps to Reproduce

1. Start the Rocket.Chat development server locally.
2. Open Rocket.Chat in the browser.
3. Create or log into a test user account.
4. Send an image with a caption from a mobile client or mobile-like environment.
5. Open the same channel from the desktop and web client.
6. Observe the image message in the desktop and web client.
7. Inspect the rendered image element using browser DevTools.

**Expected:**
The caption text should be visible above or below the image in the desktop and web client.

**Actual before fix:**
The image appeared in the desktop and web client, but the caption text was not visibly rendered. The caption appeared to exist only through image metadata or the image `alt` attribute.

---

## Solution Approach

The issue appeared to be in the desktop and web client’s attachment rendering logic. The mobile client sends the caption in a way that is preserved as image metadata or `alt` text, but the web client was not rendering that caption as visible UI text.

My approach was to make a minimal frontend change in the image attachment rendering path so that captions are displayed when available, while avoiding duplicate captions for messages that already display the same text elsewhere.

---

## Implementation Notes

### Phase I Progress

I selected Rocket.Chat issue #40730, reviewed the problem, checked that it was a suitable open-source contribution, commented on the issue expressing interest, and forked the repository.

### Phase II Progress

I set up the Rocket.Chat development environment, created the `fix-issue-40730` branch, reproduced the missing-caption behavior locally, and identified the likely affected area as the web client’s image attachment rendering flow.

### Phase III Implementation Progress

During Phase III, I worked on implementing the caption rendering fix on the `fix-issue-40730` branch.

**What I changed:**

* Added logic for handling image attachment captions in the desktop and web rendering flow.
* Made the caption visible near the image instead of leaving it only as image metadata or `alt` text.
* Preserved the image `alt` text for accessibility.
* Kept the change focused on image attachment rendering.
* Checked that images without captions still render normally.
* Checked that non-image messages are not affected by the change.

**Branch link:**
https://github.com/ZB-ZettaByte/Rocket.Chat/tree/fix-issue-40730

---

## Code Changes

### Development Branch

https://github.com/ZB-ZettaByte/Rocket.Chat/tree/fix-issue-40730

### Pull Request

**PR Status:** Not submitted yet
**Maintainer Feedback:** No maintainer feedback yet

---

## Testing Strategy

### Automated Testing

I reviewed Rocket.Chat’s existing testing patterns around frontend rendering and attachment-related behavior. I focused on making sure the fix targets the image attachment caption rendering path and does not introduce unrelated UI changes.

### Manual Testing

I manually validated the fix by repeating the original reproduction steps.

Manual validation steps:

1. Started Rocket.Chat locally.
2. Sent an image with a caption from a mobile client or mobile-like environment.
3. Opened the same channel from the desktop and web client.
4. Confirmed that the image displayed correctly.
5. Confirmed that the caption was visible near the image.
6. Confirmed that the image still preserved the correct `alt` text.
7. Confirmed that images without captions still displayed normally.
8. Confirmed that regular text messages and non-image attachments were not affected.

**Manual testing result:**
The mobile-created image caption is now visible in the desktop and web client, and existing image attachment behavior still works as expected.

---

## Challenges Faced

One challenge was identifying where the caption was stored versus where it was actually rendered. The caption appeared to be present through the image attachment metadata or `alt` text, but it was not being displayed as visible UI text.

To solve this, I traced the image attachment rendering flow and compared how Rocket.Chat handles image attachment fields, message text, and accessibility attributes. I also checked nearby attachment rendering code to keep the fix consistent with the project’s existing frontend patterns.

Another challenge was avoiding duplicate caption rendering. Since some messages may already display text separately from the attachment, I kept the change scoped so the caption is only rendered when it is needed and not already shown elsewhere.

---

## Engineering Judgment and Edge Cases Considered

I considered the following edge cases while working on the fix:

* Image attachments with no caption should not show an empty caption area.
* Image attachments with captions should still preserve the `alt` attribute for accessibility.
* Caption text should not be duplicated if it already appears in the normal message body.
* Long captions should render using existing Rocket.Chat message styling instead of custom unrelated styling.
* Non-image attachments should not be affected by this change.
* Existing desktop-created image messages should continue to render normally.

---

## Process and Communication

### Scrum and Slack Participation

I participated in Phase III communication by posting progress updates and checking for support when needed.

### Check-In Form

I submitted the Phase III check-in form and marked:

**Phase III Complete**

---

## Learnings and Reflections

### Technical Skills Gained

During Phase III, I gained more experience working inside a large TypeScript open-source codebase. I practiced tracing frontend rendering logic, making a scoped UI fix, and validating that the fix did not affect unrelated message types.

### Open Source Workflow Skills Gained

I practiced working from a fork, committing incrementally on a feature branch, keeping commits focused, documenting progress in a contribution README, and preparing the change for a pull request.

### What I'd Do Differently Next Time

Next time, I would identify the exact test file earlier in the process before starting implementation. That would make it easier to develop the fix and test case together instead of treating testing as a separate step.

---

## Resources Used

* Rocket.Chat GitHub repository
* Rocket.Chat Issue #40730
* Rocket.Chat setup documentation
* Existing Rocket.Chat message and attachment rendering code
* GitHub branch and fork workflow
* CodePath Phase III Build instructions

