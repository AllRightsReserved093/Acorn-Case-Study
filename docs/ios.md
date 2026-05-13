# iOS Client

The iOS app is built with SwiftUI and communicates with the backend through a shared API service layer.

## Major Screens and Flows

- Login and onboarding
- Event discovery feed
- Swipe-based event exploration
- Event details, bookmarks, and quick actions
- Event creation and flyer workflows
- Profile and user profile views
- Community discovery and detail pages
- Member profiles and organization tools
- Time2Meet scheduling flows
- Meeting notes and summaries

## Client-Side Engineering Focus

Key iOS engineering concerns included:

- Keeping async API calls readable and recoverable
- Avoiding inconsistent UI state after bookmark, swipe, and detail actions
- Handling authentication restoration without flashing the wrong screen
- Making complex event/community workflows usable on mobile
- Normalizing dates and images so event cards stayed visually stable

## UX Tradeoffs

The app needed to balance exploratory discovery with practical student workflows. That meant supporting both lightweight browsing and deeper flows such as creating events, joining communities, scheduling meetings, and managing notes.
