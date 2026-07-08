# Contribution 1: Editor Sticky Toolbar in Ocelot-Social

* **Contribution Number:** 1
* **Student:** Sai Rithwik Kukunuri
* **Project:** Ocelot-Social
* **Repository:** Ocelot-Social-Community/Ocelot-Social
* **Issue:** [#7127 — Feature: Editor Sticky Toolbar](https://github.com/Ocelot-Social-Community/Ocelot-Social/issues/7127)
* **Languages / Stack:** TypeScript, JavaScript, Vue
* **Labels:** good first issue, feature, design, features:post, service: frontend
* **Fork:** *To be added after fork is created*
* **Working Branch:** `feature/sticky-editor-toolbar`
* **Pull Request:** *Not submitted yet*
* **Status:** Phase I Complete — issue selected and contribution plan drafted

---

## Why I Chose This Issue

I chose Ocelot-Social issue #7127 because it is a clear user-facing frontend improvement with a realistic scope for an open-source contribution. The issue asks for the editor toolbar to stay visible while a user scrolls through longer content. This matters because when users write a longer post, group description, or comment, the formatting toolbar can scroll out of view. As a result, users may need to scroll back up just to format text or add a link.

This issue is a good fit for AI301 because it requires me to work inside a real open-source codebase, understand an existing editor component, follow the project’s frontend conventions, and make a focused UI improvement. It also matches my skills because the project uses Vue, JavaScript, and TypeScript, and the issue is labeled as a frontend good first issue.

---

## Understanding the Issue

### Problem Description

The current editor toolbar does not remain visible when users scroll down while writing longer content. If the editor content becomes long enough, the toolbar can leave the visible browser area. This creates unnecessary friction because users lose access to formatting controls while they are still actively writing or editing content.

### Expected Behavior

The editor toolbar should remain visible at the top of the browser window or editor area when the user scrolls down. Users should be able to continue formatting content without needing to scroll back up to find the toolbar.

### Current Behavior

The toolbar scrolls away with the rest of the editor content. When the user is working on longer text, they may no longer see the toolbar and must scroll upward to access formatting options again.

### Affected Areas

The affected area is the Ocelot-Social frontend, especially the editor UI used for content creation and editing.

Likely affected pages include:

* Edit post
* Edit group description
* Edit comments
* Other editor-based content areas, if they reuse the same editor component

---

## Feasibility Checklist

| Criteria                           | Evaluation                                                                          |
| ---------------------------------- | ----------------------------------------------------------------------------------- |
| Clear user-facing problem          | Yes. The toolbar becomes unavailable while scrolling through longer editor content. |
| Scope fits AI301 timeline          | Yes. This appears to be a focused frontend UI behavior change.                      |
| Good first issue                   | Yes. The issue is labeled as a good first issue.                                    |
| Project uses familiar technologies | Yes. The stack includes Vue, JavaScript, and TypeScript.                            |
| Reproduction is possible           | Likely yes. I can reproduce by creating or editing long content and scrolling.      |
| Testing path exists                | Yes. I can manually test editor behavior and check for existing frontend tests.     |
| Maintainer interaction likely      | Yes. The issue is open and part of the public Ocelot-Social repository.             |

Based on this checklist, I believe this issue is feasible for my first AI301 contribution.

---

## Phase I Progress: Issue Selection

During Phase I, I selected Ocelot-Social issue #7127 as my first contribution target.

### What I completed

* Reviewed the issue description and labels.
* Confirmed that the issue is frontend-focused.
* Confirmed that the issue is labeled as a good first issue.
* Identified the expected behavior: the editor toolbar should remain visible while scrolling.
* Identified likely affected areas: post editing, group editing, comments, and shared editor components.
* Created this Contribution README to document my issue selection and plan.

### Why this issue is valuable

This change improves the writing experience for users who create longer posts, group descriptions, or comments. Keeping the toolbar visible saves time and reduces unnecessary scrolling. It also makes the editor feel more polished and easier to use.

---

## Phase II Plan: Reproduce and Investigate

In Phase II, I will set up the Ocelot-Social development environment, reproduce the issue locally, and identify the relevant editor component.

### Environment Setup Plan

1. Fork the Ocelot-Social repository.
2. Clone my fork locally.
3. Create a working branch named `feature/sticky-editor-toolbar`.
4. Follow the project’s setup instructions.
5. Install dependencies.
6. Start the local development environment.
7. Open the webapp in the browser.
8. Create or log into a test account if needed.
9. Navigate to an editor page such as post creation or post editing.

### Reproduction Steps

1. Start the Ocelot-Social development environment locally.
2. Open the webapp in the browser.
3. Go to a page that uses the editor, such as creating or editing a post.
4. Enter enough text to make the page scroll.
5. Scroll down while editing the content.
6. Observe whether the toolbar stays visible or scrolls out of view.

### Expected Result

The toolbar should remain visible while scrolling so that formatting controls are always accessible.

### Actual Result Before Fix

The toolbar likely scrolls out of view with the rest of the editor content, forcing the user to scroll back up to access formatting options.

---

## Initial Solution Approach

My initial approach is to make the editor toolbar sticky using the project’s existing frontend structure and styling conventions.

The likely implementation path is:

1. Locate the editor component used for posts, comments, and group descriptions.
2. Identify the toolbar element inside the editor.
3. Check whether the toolbar is shared across multiple editor pages.
4. Apply sticky behavior to the toolbar using existing styling patterns.
5. Ensure the toolbar does not cover editor content while sticky.
6. Test the behavior on longer posts and shorter posts.
7. Check whether the behavior works across the affected pages listed in the issue.

The main goal is to make a minimal, maintainable frontend change rather than adding unnecessary custom behavior.

---

## Engineering Considerations

I will need to be careful about several details while implementing this feature:

* The toolbar should stay visible while scrolling.
* The toolbar should not overlap or hide the editor content.
* The sticky behavior should work only where appropriate.
* The change should not break short editor forms.
* The toolbar should still look consistent with the existing design.
* The solution should reuse existing CSS, Vue, and component patterns where possible.
* The change should work across editor pages if they share the same component.
* The implementation should avoid hardcoded layout values unless they are already part of the project’s design system.

---

## Testing Strategy

### Manual Testing

I plan to manually test the feature using the original issue scenario.

Manual test cases:

1. Create or edit a short post.
2. Confirm the toolbar still appears normally.
3. Create or edit a long post.
4. Scroll down while editing.
5. Confirm the toolbar remains visible.
6. Test adding formatting while scrolled down.
7. Test adding a link while scrolled down.
8. Check whether the sticky toolbar affects the content layout.
9. Test the editor in other possible areas, such as group descriptions or comments, if available.
10. Confirm there are no obvious visual regressions.

### Automated Testing

After identifying the relevant component, I will check whether Ocelot-Social has existing frontend tests for the editor. If there is an appropriate test pattern, I will consider adding or updating a test. If the change is mainly CSS/UI behavior and automated testing is not practical, I will document manual before-and-after evidence clearly in the pull request.

---

## Pull Request Plan

When the implementation is ready, I will open a pull request against the upstream Ocelot-Social repository.

### Planned PR Title

`feat(editor): make toolbar sticky while scrolling`

### Planned PR Description Summary

This PR will make the editor toolbar stay visible while users scroll through longer editor content. The goal is to improve the writing and editing experience for longer posts, group descriptions, comments, and other editor-based content areas.

### Planned Issue Reference

`Closes #7127`

### Planned Acceptance Criteria

* The editor toolbar remains visible while scrolling through long editor content.
* Users can access formatting controls without scrolling back to the top.
* Short editor content still displays normally.
* The toolbar does not cover or block editor content.
* Existing editor styling remains consistent.
* The change does not break other editor-based pages.
* Manual before-and-after testing is documented.

---

## Maintainer Feedback Log

| Date         | Feedback / Action                                            | Student Response                                                                   |
| ------------ | ------------------------------------------------------------ | ---------------------------------------------------------------------------------- |
| July 8, 2026 | Selected Ocelot-Social issue #7127 for AI301 Contribution 1. | Created Contribution README and initial implementation plan.                       |
| July 8, 2026 | Issue reviewed for scope, feasibility, and technical fit.    | Determined that it is a good first frontend issue using Vue/JavaScript/TypeScript. |
| TBD          | Pull request submitted.                                      | TBD                                                                                |
| TBD          | Maintainer feedback received.                                | TBD                                                                                |

---

## Current Status

The issue has been selected and documented for Phase I. My next step is to set up the Ocelot-Social development environment, reproduce the toolbar scrolling behavior, and identify the editor component that controls the toolbar.

Current status:

**Phase I Complete — Issue selected and contribution README drafted.**

Next step:

**Phase II — Reproduce the issue locally and write a more specific implementation plan.**

---

## Challenges I Expect

One challenge may be finding the exact editor component because the toolbar may be part of a shared editor package or nested frontend component. I will need to trace how posts, comments, and group descriptions use the editor.

Another challenge may be applying sticky behavior without causing layout issues. A toolbar that sticks to the top of the page can accidentally overlap content if spacing is not handled carefully. I will test the behavior with both short and long content to make sure the UI still feels natural.

I may also need to check whether the toolbar should stick to the browser window, the editor container, or another layout boundary. I will use the issue description and existing design patterns in the codebase to make that decision.

---

## AI Tool Usage Plan

I will use AI tools to support my work, but I will remain responsible for every line of code I submit.

I may use AI tools to:

* Understand unfamiliar Vue components.
* Summarize editor-related files.
* Compare existing styling patterns.
* Draft possible test cases.
* Review my pull request description.
* Check whether my implementation is consistent with the issue.

I will not submit code that I do not understand. Before opening the pull request, I will manually review the final changes, run available checks, and confirm that the behavior matches the issue requirements.

---

## Learnings and Reflection

### What I expect to learn

Through this contribution, I expect to learn how a real open-source Vue application organizes editor components, styling, and frontend behavior. I also expect to practice reading unfamiliar code, making a small but meaningful UI change, and communicating my work clearly in a pull request.

### Why this contribution matters

This contribution matters because it improves the usability of the editor. Users writing longer content should not have to interrupt their writing flow just to scroll back to the toolbar. A sticky toolbar is a small improvement, but it can make the editor feel much smoother and more professional.

### Portfolio Value

This contribution will show that I can:

* Select a feasible open-source issue.
* Understand a real frontend codebase.
* Improve a user-facing feature.
* Work with Vue, JavaScript, TypeScript, and project-specific conventions.
* Document my process professionally.
* Prepare a pull request for maintainer review.
