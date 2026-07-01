# Contribution 1: Mobile image caption alt text not displayed on desktop and web clients

* **Contribution Number:** 1
* **Student:** Sai Rithwik Kukunuri
* **Issue:** Rocket.Chat Issue #40730
* **Fork:** https://github.com/ZB-ZettaByte/Rocket.Chat
* **Working Branch:** https://github.com/ZB-ZettaByte/Rocket.Chat/tree/fix-issue-40730
* **Status:** Phase IV Complete — PR submitted and awaiting review

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

### Phase IV Submission Progress

During Phase IV, I prepared the contribution for formal pull request submission.

**What I completed:**

* Submitted the pull request against the upstream Rocket.Chat repository.
* Referenced the related issue using `Closes #40730`.
* Wrote a PR description that explains why the fix is needed before describing what changed.
* Included an acceptance criteria checklist in the PR description.
* Documented the current PR status in this README.
* Added a maintainer feedback log.
* Submitted the Phase IV check-in form and marked **Phase IV Complete**.

---

## Code Changes

### Development Branch

https://github.com/ZB-ZettaByte/Rocket.Chat/tree/fix-issue-40730

### Pull Request

**PR Status:** Open and awaiting review

**Related Issue:** Rocket.Chat Issue #40730

**Issue Reference in PR:** Closes #40730

**PR Summary:**
This pull request fixes a user-facing caption rendering issue in Rocket.Chat’s desktop and web client. When an image with a caption is sent from the mobile app, the caption should be visible when the same message is viewed on desktop or web. The change updates the image attachment rendering flow so available caption text is displayed near the image while preserving the image `alt` text for accessibility.

**Current Status:**
The PR has been submitted to the upstream Rocket.Chat repository and is currently awaiting maintainer review. No maintainer feedback has been received yet.

---

## Pull Request Description Summary

### Why this PR was needed

Rocket.Chat users can send images with captions from the mobile app, but those captions were not visibly displayed in the desktop and web client. This created an inconsistent experience across clients because the caption information existed in the attachment metadata or `alt` text, but it was not shown as readable message content in the web UI.

### What this PR changes

This PR updates the image attachment rendering path so caption text is displayed near the image when available. The fix keeps the image `alt` text for accessibility and avoids changing unrelated message or attachment behavior.

### Acceptance Criteria

* Image captions sent from mobile are visible in the desktop and web client.
* Image `alt` text is still preserved for accessibility.
* Images without captions continue to render normally.
* Regular text messages are not affected.
* Non-image attachments are not affected.
* No breaking changes are introduced.

### Before / After Evidence

**Before fix:**
The image appeared in the desktop and web client, but the caption text was not visibly rendered.

**After fix:**
The image still appears normally, and the caption text is visible near the image in the desktop and web client.

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

## Maintainer Feedback Log

| Date         | Feedback / Action                                                               | Student Response                                                      |
| ------------ | ------------------------------------------------------------------------------- | --------------------------------------------------------------------- |
| July 1, 2026 | Pull request submitted to the upstream Rocket.Chat repository for Issue #40730. | Added PR summary, current status, and issue reference to this README. |
| July 1, 2026 | PR was surfaced for review through the pull request submission process.         | Waiting for maintainer review.                                        |
| July 1, 2026 | No maintainer feedback received yet.                                            | Current status remains: awaiting review.                              |

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

I participated in Phase III and Phase IV communication by posting progress updates, checking for support when needed, preparing the pull request, and documenting the current review status.

### Reviewer / Maintainer Communication

After submitting the pull request, I made the contribution visible for review through the upstream PR process. As of now, no maintainer feedback has been received yet, so the PR status is **awaiting review**.

### Check-In Form

I submitted the Phase IV check-in form and marked:

**Phase IV Complete**

---

## Learnings and Reflections

### Technical Skills Gained

During this contribution, I gained more experience working inside a large TypeScript open-source codebase. I practiced tracing frontend rendering logic, understanding how image attachments are displayed, and making a scoped UI change without affecting unrelated message types.

I also learned more about the difference between accessibility metadata and visible UI content. In this issue, the caption information appeared to exist through attachment metadata or the image `alt` text, but that did not automatically mean users could see it in the desktop and web client.

### Open Source Workflow Skills Gained

I practiced the full open-source contribution workflow: selecting an issue, forking the repository, creating a feature branch, reproducing the bug, making a focused fix, preparing a pull request, referencing the issue properly, and documenting the work in a contribution README.

I also learned that submitting a pull request is not the same as having it merged. A PR can still be a valid contribution milestone while it is awaiting maintainer review, as long as the work is clearly documented and ready for review.

### What I'd Do Differently Next Time

Next time, I would identify the exact test file earlier in the process before starting implementation. That would make it easier to develop the fix and test case together instead of treating testing as a separate step.

I would also prepare before-and-after evidence earlier, such as screenshots or short screen recordings. Since this was a UI issue, visual evidence would make the pull request easier for maintainers and reviewers to evaluate quickly.
