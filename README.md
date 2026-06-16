# Contribution 1: Mobile image caption (alt text) not displayed on desktop/web clients

- **Contribution Number:** 1
- **Student:** Sai Rithwik Kukunuri
- **Issue:** Rocket.Chat Issue #40730
- **Fork:** https://github.com/ZB-ZettaByte/Rocket.Chat
- **Working Branch:** https://github.com/ZB-ZettaByte/Rocket.Chat/tree/fix-issue-40730
- **Status:** Phase II Complete

---

## Why I Chose This Issue

I chose this issue because it is a clear user-facing bug in Rocket.Chat’s desktop/web client. When users send an image with a caption from the mobile app, the caption should still be visible when the message is viewed from desktop or web. Fixing this would improve consistency across Rocket.Chat clients and make image messages easier to understand.

This issue also matches my skills and learning goals because Rocket.Chat is a large TypeScript-based open-source project, and the bug appears related to frontend message and image attachment rendering. I want to learn how a real production chat platform handles message attachments across mobile and web clients while practicing the full open-source contribution workflow.

---

## Understanding the Issue

### Problem Description

When a user sends an image with a caption from the Rocket.Chat mobile app, the caption text is not displayed visibly in the desktop/web client. According to the issue, the caption appears to be stored in the image’s `alt` attribute, but it is not rendered as normal visible text near the image.

### Expected Behavior

The caption text should be visible on the desktop/web client when viewing an image that was sent with a caption from the mobile app. The caption should appear either above or below the image so users can read it clearly.

### Current Behavior

The image appears in the desktop/web client, but the caption text is missing from the visible message UI. The caption appears to exist only as image `alt` text instead of being displayed as readable message content.

### Affected Components

The affected area is likely Rocket.Chat’s web client message rendering flow, especially the components responsible for displaying image attachments or file attachments inside messages.

---

## Reproduction Process

### Environment Setup

I set up the Rocket.Chat development environment and created a working branch in my fork.

**Working branch:**
https://github.com/ZB-ZettaByte/Rocket.Chat/tree/fix-issue-40730

Setup notes:

* I cloned my fork of Rocket.Chat.
* I installed the required project dependencies based on the Rocket.Chat setup instructions.
* I started the development server and verified that Rocket.Chat was accessible locally.
* No major setup issues or blockers were encountered.

### Steps to Reproduce

1. Start the Rocket.Chat development server locally.
2. Open Rocket.Chat in the browser.
3. Create or log into a test user account.
4. Open Rocket.Chat from a mobile client or mobile-like environment.
5. Send an image with a caption, such as `Test caption from mobile`, into a test channel.
6. Open the same channel from the desktop/web client.
7. Observe the image message in the desktop/web client.
8. Inspect the rendered image element using browser DevTools.

**Expected:**
The caption text should be visible above or below the image in the desktop/web client.

**Actual:**
The image appears in the desktop/web client, but the caption text is not visibly rendered. The caption appears to be stored only in the image `alt` attribute instead of being displayed as normal message text.

### Reproduction Evidence

**Branch:**
https://github.com/ZB-ZettaByte/Rocket.Chat/tree/fix-issue-40730

**Findings:**

* I was able to reproduce the issue locally.
* The image sent with a caption from mobile appears in the desktop/web client.
* The caption is not shown as visible text in the message UI.
* The caption appears to be available through the image `alt` attribute, but the web client does not render it as a visible caption.

---

## Solution Approach

### Analysis

Based on the reproduction, the issue appears to be in the desktop/web client’s image attachment rendering flow. The mobile client sends or stores the caption in a way that becomes available as the image `alt` text, but the desktop/web client does not display that value as visible caption text.

The root cause is likely that the web client renders the image attachment itself but does not separately render the caption metadata when the caption comes from a mobile-created image message.

---

## Implementation Plan

Using the UMPIRE framework:

### Understand

The problem is that image captions sent from the mobile app are not visible in the desktop/web client. The caption appears to exist as image metadata or `alt` text, but it is not displayed as readable text near the image.

### Match

I will inspect Rocket.Chat’s existing message and attachment rendering components to find how image attachments are displayed. I will compare:

* How mobile-created image messages store captions.
* How desktop-created messages display normal message text.
* How existing attachment metadata, file descriptions, and image attributes are rendered in the web client.

### Plan

1. Locate the web client component responsible for rendering image attachments inside messages.
2. Identify where the image `alt` text or attachment metadata is passed into the rendered image component.
3. Add logic to render the caption visibly when a mobile-created image attachment includes caption text.
4. Make sure the caption is not duplicated for messages that already display text separately.
5. Keep the UI change minimal and consistent with Rocket.Chat’s existing message styling.
6. Add or update tests if there are existing tests for attachment or message rendering.
7. Manually verify that image captions sent from mobile appear correctly in desktop/web.
8. Confirm that images without captions still render normally.

### Implement

Implementation will begin in Phase III on the `fix-issue-40730` branch.

### Review

Before opening a pull request, I will review Rocket.Chat’s contribution guidelines, TypeScript conventions, formatting expectations, and existing PR requirements. I will also compare my changes against nearby message rendering code to keep the implementation consistent with the project’s style.

### Evaluate

I will verify the fix by repeating the reproduction steps:

1. Send an image with a caption from mobile.
2. Open the same message in desktop/web.
3. Confirm the caption is visible near the image.
4. Confirm the image still keeps the correct `alt` text for accessibility.
5. Confirm images without captions still display normally.
6. Run relevant existing tests or the project’s recommended test command if applicable.

---

## Testing Strategy

### Unit Tests

Planned after identifying the affected component:

* Test that image captions are rendered when present.
* Test that images without captions still render normally.
* Test that captions are not duplicated when message text is already displayed elsewhere.
* Test that existing message attachment rendering behavior is not broken.

### Integration Tests

To be determined after reviewing Rocket.Chat’s existing test structure for message and attachment rendering.

### Manual Testing

Manual testing plan:

1. Send an image with a caption from mobile.
2. Open the same message in the web/desktop client.
3. Confirm the caption is visible.
4. Confirm images without captions still display correctly.
5. Confirm normal text messages and desktop-created image messages are not affected.

---

## Implementation Notes

### Phase I Progress

I selected Rocket.Chat issue #40730, commented on the issue expressing interest, and forked the repository.

### Phase II Progress

I set up the Rocket.Chat development environment, created a working branch, reproduced the missing-caption behavior, and wrote an implementation plan for the fix.

### Code Changes

No code changes yet. Code changes will begin in Phase III after this reproduction and planning phase.

### Pull Request

**PR Link:** Not submitted yet.
**PR Description:** To be written after implementation.
**Maintainer Feedback:** No maintainer feedback yet.

---

## Learnings & Reflections

### Technical Skills Gained

So far, I learned how to evaluate open-source issues, check whether an issue is unassigned, inspect whether there are linked branches or pull requests, fork a large production repository, create a working branch, and reproduce a frontend bug locally.

### Challenges Overcome

The main challenge in Phase I was choosing a suitable issue from many open-source repositories. I compared several projects and selected Rocket.Chat because it is an active TypeScript-based open-source project with a clear user-facing bug.

For Phase II, I focused on setting up the project, reproducing the behavior, and narrowing the likely affected area to the web client’s image attachment rendering flow.

### What I'd Do Differently Next Time

Next time, I would start by filtering for small bugs with clear reproduction steps, no assignee, and no linked pull requests earlier in the issue selection process. I would also check the setup instructions and development workflow earlier to estimate setup difficulty before choosing the issue.

---

## Resources Used

* Rocket.Chat GitHub repository
* Rocket.Chat Issue #40730
* Rocket.Chat setup documentation
* GitHub branch and fork workflow
