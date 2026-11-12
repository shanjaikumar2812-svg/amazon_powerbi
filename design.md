# Library Management System — UI Design Specification

## Purpose

Redesign the existing Library Management System as a calm, practical, professional tool for library staff. The interface should feel intentionally designed by a human product designer—not like a generic AI-generated SaaS template.

This document is the source of truth for UI decisions. Follow it consistently across every screen.

## Product and technical context

- Existing stack: HTML, CSS, vanilla JavaScript, PHP, and MySQL.
- The application runs locally with XAMPP/WAMP.
- Preserve the current stack, database, and working features unless a change is necessary and explicitly documented.
- Existing core workflows include viewing/searching books, filtering by category and availability, adding books, changing Available/Issued status, and deleting books.
- Inspect the existing project before changing the UI. Reuse real fields and real capabilities.
- Do not represent a visual prototype as connected to the database unless it really is.

## Design principles

1. **Utility before decoration.** Every visible element must help users understand the collection or complete a real task.
2. **Quiet confidence.** Use a restrained palette, typography, spacing, and clear hierarchy instead of gradients, glowing effects, or decorative graphics.
3. **Real data only.** Do not invent statistics, reviews, ratings, borrower details, activity feeds, trends, or analytics.
4. **No dead controls.** Every visible button, link, filter, menu, tab, and icon must perform a real, defined action. If a feature is not implemented, do not display its control.
5. **Consistency.** Reuse the same spacing, type scale, button styles, form controls, tables, and status indicators across all screens.
6. **Accessibility.** Keep text readable, contrast sufficient, keyboard navigation available, and focus states visible.
7. **Responsive by design.** Support desktop, tablet, and mobile without squeezing desktop layouts onto a phone.

## Visual identity

### Color palette

Use a neutral, editorial palette with a muted green accent. **Do not use blue gradients or any gradient backgrounds.**

- Page background: `#F5F5F0` (warm off-white)
- Surface / cards: `#FFFFFF`
- Primary text: `#252923` (near-black green-grey)
- Secondary text: `#666D64`
- Borders and dividers: `#E2E5DD`
- Primary accent: `#456B50` (muted forest green)
- Accent hover: `#365640`
- Soft accent background: `#EDF2EA`
- Available status: text `#28623B`, background `#E8F3E8`
- Issued status: text `#875B18`, background `#F8EFD9`
- Error / destructive: text `#A3332A`, background `#F8E9E7`
- Focus ring: a clearly visible, accessible outline based on the accent color

Use color sparingly and semantically. Do not use a rainbow palette. Avoid saturated neon green, electric blue, purple, pink, or multicolor KPI cards.

### Strictly avoid

- Blue gradients, purple gradients, mesh gradients, and gradient backgrounds
- Glassmorphism, glow effects, neon borders, and oversized blur shadows
- Decorative blobs, floating shapes, random geometric ornaments, and unnecessary background patterns
- Generic AI-dashboard styling with a row of colorful KPI cards, excessive rounded pills, and a chart on every screen
- Excessive cards nested inside other cards
- Huge hero headings that waste space in an admin tool
- Emojis used as interface icons
- Random stock photos, fake book covers, and decorative illustrations that do not help identify a real book
- Fake reviews, fake ratings, testimonials, fabricated activity, made-up trends, or made-up percentage changes
- Placeholder metrics such as “+24% this month” without a real source and valid calculation
- Unnecessary buttons such as Upgrade, Invite Team, Export, Notifications, Help, AI Assistant, or Add Member unless the existing product genuinely supports them
- Buttons that do nothing, links to `#`, empty settings pages, or controls included only to make a screen look busy

## Typography and layout

- Use Inter if already available, otherwise use a reliable system sans-serif stack. Do not add a font dependency solely for decoration.
- Body text: approximately 14–16px.
- Table text: approximately 13–14px, with comfortable line height.
- Page titles: approximately 24–28px, medium/semi-bold rather than oversized.
- Section titles: approximately 16–18px.
- Labels and metadata: approximately 12–13px, with adequate contrast.
- Use a consistent spacing scale based on 4px or 8px increments.
- Prefer 8–12px corner radii. Avoid making every element a pill.
- Use thin borders and very subtle shadows only when needed to establish hierarchy.
- Keep content aligned to a clear grid and avoid arbitrary positioning.
- Use whitespace intentionally, but do not leave huge empty areas or make tables unnecessarily sparse.
- Keep animations brief and functional. Respect `prefers-reduced-motion`.

## Navigation and application shell

Create a restrained desktop layout:

- A compact, dark forest-green or neutral sidebar—not blue.
- Show the application name and a simple, understated library mark.
- Only include these navigation items if they map to implemented screens: Dashboard, Books, and Categories.
- Add Book should be a primary action or form flow, not a duplicate navigation item if that creates clutter.
- Do not show Settings unless actual settings exist.
- Use clear active navigation styling without glow or gradients.
- Keep the top bar minimal. Show only contextually useful items such as page title/breadcrumb, search where relevant, and the main action for that screen.
- Do not add a fake profile, avatar, notification bell, help menu, or user account menu if authentication and those features do not exist.
- On mobile, use a simple accessible navigation drawer or compact menu.

## Screen specifications

### 1. Dashboard

Purpose: let staff quickly understand the current collection and move into common tasks.

Include:
- Page title: `Library overview`
- A short practical subtitle, if useful.
- A small row or grid of real summary figures:
  - Total books
  - Available books
  - Issued books
  - Categories
- Calculate these figures from the actual database. Do not hardcode them.
- Ensure Available + Issued = Total if the current schema uses one status per book.
- A recent-books list only if actual creation timestamps exist. Otherwise, use a simple “All books” or “Recently added” section only when its ordering is supported by the data.
- A useful book-list preview or a concise category summary only if it adds real value.
- Quick actions limited to real common tasks, such as `Add book` and `View all books`.

Do not add charts just to fill space. Do not display fake activity feeds, percentage changes, trends, reviews, popularity scores, or fabricated “insights.” If there is not enough real data for a chart, omit it.

### 2. Book inventory

This is the main working screen. Prioritize usability over decoration.

Include:
- Page title: `Books`
- A single prominent search field that searches real supported fields, such as book ID, title, and author.
- Category filter based on actual categories in the database.
- Availability filter with `All`, `Available`, and `Issued`.
- Sort options only for fields that exist.
- A clear-filters action shown only when filters are active.
- A readable, properly aligned table with columns matching the real schema, such as:
  - Book ID
  - Title
  - Author
  - Category
  - Status
  - Actions
- Compact status labels, not oversized pills.
- A simple action menu or small, clearly labelled actions for supported operations.
- Pagination only if implemented and useful for the dataset.
- An honest empty state when no records match the filters.
- Loading and error states for actual API requests.

Do not add ratings, reviews, borrower names, due dates, popularity, stock quantities, ISBNs, or cover images unless the data model actually stores them.

Do not force a grid/table toggle if one clear table is better for staff workflows. Do not add export, bulk actions, or advanced filters unless fully implemented and genuinely useful.

### 3. Add and edit book

Use a clean form in a focused panel or modal.

Show only fields supported by the current schema, for example:
- Book ID
- Title
- Author
- Category
- Availability, if appropriate for the current workflow

Requirements:
- Explicit labels, not placeholder-only fields.
- Required indicators where fields are required.
- Inline validation with clear error messages.
- A single primary submit button with a specific label such as `Save book`.
- A secondary `Cancel` action.
- Disabled/loading state during submission.
- Success or failure feedback based on the real API response.
- Prevent duplicate submissions and duplicate IDs.
- Keep entered values if a request fails.

Do not add unrelated fields such as publisher, ISBN, price, shelf location, cover upload, or publication year unless the backend and database are updated to support them correctly.

### 4. Issue, return, and delete

- Show `Issue` only for an available book and `Return` only for an issued book, according to the actual existing status model.
- Confirm important state changes when needed.
- Use a clear confirmation dialog for deletion that names the selected book.
- Make destructive actions visually distinct but not dramatic.
- Update the screen and summary figures only after the server confirms success.
- Show useful error feedback if the operation fails.
- Prevent repeated submissions while a request is in progress.
- Do not invent borrower identity, loan history, due dates, fines, or reservation details.

### 5. Categories

- List categories derived from actual book records.
- Show the category name and a count calculated from real records, if useful.
- Allow a category to filter the inventory.
- Do not show decorative category cards with fabricated totals.
- Do not expose category creation/editing controls unless that workflow is implemented end-to-end.

### 6. States that must be designed

Provide consistent visual states for:
- Normal content
- Hover and keyboard focus
- Loading
- Empty search results
- No books in the database
- Validation errors
- API/database errors
- Successful save/update
- Delete confirmation
- Mobile navigation open and closed

Messages should be concise and human, for example: “No books match these filters. Clear filters to see the full collection.” Avoid robotic marketing copy.

## Interaction rules

- Every visible control must have a defined, working action.
- Prefer direct labels over icon-only controls. If an icon-only control is necessary, provide an accessible name and tooltip.
- Do not use generic labels such as “Learn more” unless there is a real destination.
- Avoid repeated primary buttons in the same section.
- Use one clear primary action per screen or dialog.
- Make cancellation and destructive actions clear.
- Ensure modals can be closed by keyboard and have appropriate focus behavior.
- Keep search, filters, and status changes understandable and predictable.

## Responsive behavior

- Desktop: stable sidebar and comfortable table layout.
- Tablet: reduced sidebar width and sensible table adaptation.
- Mobile: compact navigation, stacked summary figures, single-column forms, large enough touch targets, and a book list/table adapted for narrow screens.
- Prevent page-level horizontal overflow.
- Do not shrink all desktop columns until they become unreadable.

## Implementation and integration guardrails

This UI belongs to an existing HTML/CSS/vanilla JavaScript + PHP + MySQL application.

- Inspect the current files and schema before designing or implementing changes.
- Preserve existing working functionality and local XAMPP/WAMP compatibility.
- Do not replace the stack with React, Node.js, Firebase, or a hosted backend just to match a design.
- Use the real API and database fields.
- Never hardcode KPI values into the final application.
- Never claim an operation succeeded before the API confirms it.
- Keep database credentials server-side.
- Escape user-controlled values and validate on the server.
- If Stitch is only producing a design/prototype, clearly treat sample content as visual-only and do not imply database integration.

## Final acceptance checklist

- [ ] No blue or other gradient backgrounds.
- [ ] No fake reviews, ratings, testimonials, trends, or percentage changes.
- [ ] No fabricated library statistics or activity.
- [ ] No unwanted, redundant, or nonfunctional buttons.
- [ ] No fake user profile or notification controls.
- [ ] All labels and data fields match the actual application.
- [ ] The visual system is consistent across screens.
- [ ] The interface looks like a practical, intentionally designed library tool—not a generic AI-generated dashboard.
- [ ] Desktop and mobile layouts are both usable.
- [ ] Existing functionality and database compatibility are preserved.

Prioritize clarity, authenticity, restraint, and real workflows over visual effects. When unsure whether to add an element, leave it out unless it solves a real user need.
