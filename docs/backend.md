# Backend

The backend is a Python Flask service. It exposes REST APIs used by the iOS client and integrates with Google Cloud services.
Most backend API definitions and service implementations in this project were implemented by me.

## Backend Responsibilities

- Verify Google ID tokens and issue app session tokens
- Store and retrieve profiles, events, follows, communities, and meeting notes
- Serve event discovery, search, likes, bookmarks, reports, and post creation flows
- Provide community membership and organization workflows
- Support Time2Meet scheduling polls
- Run event ingestion and seed jobs
- Provide AI-assisted endpoints for search, copy generation, flyer workflows, and summaries

## Deployment Shape

The backend was designed for Google App Engine-style deployment, with local development using environment variables and a Python virtual environment.

Typical environment categories:

- Google OAuth client ID
- Flask secret key
- AI provider API key
- local development auth bypass token
- Datastore project/database configuration
- seed/admin protection secrets

## Reliability Work

Backend reliability work included schema compatibility fixes, ingestion fixes, date parsing normalization, and local development documentation. These changes mattered because the iOS client depended on stable API behavior while features were changing quickly.

## Loading Performance Optimization

Backend-side loading optimization focused on reducing long-tail latency and improving overall event load speed:

- local backend cache for frequently requested simplified description text, metadata, and thumbnails instead of refetching each time
- tiered loading strategy, such as loading thumbnails first and deferring heavier assets
- segmented event loading instead of loading the full event set in one pass
- partial-load tolerance for unstable network, unusually large files, and unpredictable client-side issues, so available content could be shown before every asset finished

This was coordinated with the client side as a progressive display strategy similar to streaming UX: render what is already available instead of blocking on full completion.

No formal statistical study was run for this area. Based on repeated end-to-end testing and usage, the changes removed intermittent ultra-long waits and made activity loading feel near-instant in most normal cases.
