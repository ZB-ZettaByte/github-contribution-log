# Contribution 1: Mobile image caption (alt text) not displayed on desktop/web clients

- **Contribution Number:** 1
- **Student:** Sai Rithwik Kukunuri
- **Issue:** [Rocket.Chat Issue #40730](https://github.com/RocketChat/Rocket.Chat/issues/40730)
- **Fork:** [ZB-ZettaByte/Rocket.Chat](https://github.com/ZB-ZettaByte/Rocket.Chat)
- **Status:** Phase I Complete

---

## Why I Chose This Issue

I chose this issue because it is a clear user-facing bug in Rocket.Chat’s desktop/web client. When users send an image with a caption from the mobile app, the caption should still be visible when the message is viewed from desktop or web. Fixing this would improve consistency across Rocket.Chat clients and make image messages easier to understand.

This issue also matches my skills and learning goals because Rocket.Chat is a large TypeScript-based open-source project, and the bug appears related to frontend message/image rendering. I want to learn how a real production chat platform handles message attachments across mobile and web clients while practicing the full open-source contribution workflow.

---

## Understanding the Issue

### Problem Description

When a user sends an image with a caption from the Rocket.Chat mobile app, the caption text is not displayed visibly in the desktop/web client. According to the issue, the caption appears to be stored in the image’s `alt` attribute, but it is not rendered as normal visible text near the image.

### Expected Behavior

The caption text should be visible on the desktop/web client when viewing an image that was sent with a caption from the mobile app. The caption should appear either above or below the image so users can read it clearly.

### Current Behavior

The image appears in the desktop/web client, but the caption text is missing. The caption seems to exist only as `alt` text on the image instead of being shown as visible message content.

### Affected Components---

## Reproduction Process

### Environment Setup

Not started yet. This will be completed in Phase II after setting up the Rocket.Chat development environment locally.

### Steps to Reproduce

Planned for Phase II:

1. Run Rocket.Chat locally.
2. Open Rocket.Chat from a mobile client or mobile-like environment.
3. Send an image with a text caption.
4. Open the same channel from the desktop/web client.
5. Confirm whether the image caption is missing in the web client.

### Reproduction Evidence

* **Commit showing reproduction:** Not available yet.
* **Screenshots/logs:** Not available yet.
* **My findings:** To be documented in Phase II after reproducing the issue locally.

---

## Solution Approach

### Analysis

Initial analysis based on the issue description: the caption sent from the mobile app appears to be stored as the image’s `alt` text, but the desktop/web client does not render that caption as visible message content. I will confirm the exact root cause after reproducing the issue locally.

### Proposed Solution

Not finalized yet. My expected approach is to inspect the web client’s image/message rendering flow and identify where image captions or attachment metadata should be rendered.

### Implementation Plan

Using the UMPIRE framework:

**Understand:**
The problem is that image captions sent from mobile are not visible in the desktop/web client, even though the caption appears to exist as image metadata or `alt` text.

**Match:**
During Phase II, I will look for similar message attachment rendering patterns in the Rocket.Chat codebase, especially how image attachments, file descriptions, and message bodies are displayed.

**Plan:**
Planned steps for Phase II/III:

1. Set up Rocket.Chat locally.
2. Reproduce the missing-caption behavior.
3. Locate the web client component responsible for rendering image attachments.
4. Compare mobile-created image messages with desktop-created image messages.
5. Identify where the caption should be passed or displayed.
6. Implement a small fix.
7. Test the fix manually and with existing tests if applicable.

**Implement:**
Not started yet. Implementation will begin in Phase III.

**Review:**
I will review Rocket.Chat’s contribution guidelines, TypeScript conventions, formatting expectations, and PR requirements before submitting changes.

**Evaluate:**
I will verify the fix by sending an image with a caption and confirming that the caption appears correctly in the desktop/web client.

---

## Testing Strategy

### Unit Tests

Planned after identifying the affected component:

* [ ] Test that image captions are rendered when present.
* [ ] Test that images without captions still render normally.
* [ ] Test that existing message attachment rendering behavior is not broken.

### Integration Tests

To be determined after reviewing the existing Rocket.Chat test structure.

### Manual Testing

Planned manual testing:

1. Send an image with a caption from mobile.
2. Open the same message in the web/desktop client.
3. Confirm the caption is visible.
4. Confirm images without captions still display correctly.

---

## Implementation Notes

### Phase I Progress

Selected Rocket.Chat issue #40730, commented on the issue expressing interest, and forked the repository.

### Code Changes

No code changes yet. Code changes will begin after reproducing the issue locally in Phase II.

---

## Pull Request

**PR Link:** Not submitted yet.

**PR Description:** To be written after implementation.

**Maintainer Feedback:** No maintainer feedback yet.

**Status:** Not started.

---

## Learnings & Reflections

### Technical Skills Gained

So far, I learned how to evaluate open-source issues, check whether an issue is unassigned, inspect whether there are linked branches or pull requests, and follow a project’s contribution workflow.

### Challenges Overcome

The main challenge in Phase I was choosing a suitable issue from many open-source repositories. I compared several projects and selected Rocket.Chat because it is an active TypeScript-based open-source project with a clear user-facing bug.

### What I'd Do Differently Next Time

Next time, I would start by filtering for small bugs with clear reproduction steps, no assignee, and no linked pull requests earlier in the issue selection process.


The affected area is likely the Rocket.Chat web client’s message rendering flow, especially the components responsible for displaying image attachments or file attachments inside messages. I will identify the exact files and components during Phase II after setting up the project locally and reproducing the issue.



---

## Resources Used

- [Link to helpful documentation]
- [Tutorial or Stack Overflow post that helped]
- [GitHub issues or discussions that helped]
