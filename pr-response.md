# PR Response Doc — CineLog Watchlist Feature

## AI Usage
<!-- Fill in at the end — how you used AI tools during this project -->
<!-- Describe at least 2 specific instances where you used an AI tool during this project. 
     For each: what did you give the AI as input, what did it produce, and what did you
     change, override, or direct differently?

     "I used Claude to help me code" is not sufficient.
     "I gave Claude my X section from planning.md and asked it to implement
     function(). It returned a function using Y. I overrode the
     Z because AA" -->

**Instance 1**:

- *What I gave the AI:* 
- *What it produced:* 
- *What I changed or overrode:* 

**Instance 2**:

- *What I gave the AI:* 
- *What it produced:* 
- *What I changed or overrode:*

## Comment 1 — Rename
**What I did:**
- Renamed the helper method from `save_to_watchlist` to `add_to_watchlist` to better reflect the operation and match the watchlist feature naming.
- Updated all references across the codebase so the rename was consistent in routes, services, and tests.
- Confirmed the new method name fits the existing API semantics and is easier to understand for future maintainers.
**How I verified:**
- Ran the existing unit tests and confirmed the watchlist-related tests still passed after the rename.
- Completed a quick manual review of the route and service files to ensure there were no lingering `save_to_watchlist` references.

## Comment 2 — Deduplication
**What I did:**
- Added duplicate-entry detection in `services/watchlist_service.py` before creating a new `WatchlistEntry`.
- Raised a new `AlreadyInWatchlistError` when the same film is already on the user's watchlist.
- Updated `routes/watchlist/watchlist.py` to map the duplicate error to a `409 Conflict` response.
**How I verified:**
- Reviewed the watchlist service logic to ensure the existing query check mirrors `add_to_collection()`.
- Confirmed routes now handle duplicate watchlist adds consistently with collection error handling.

## Comment 3 — Missing test
**What I did:**
**How I verified:**

## Comment 4 — Default visibility
**My position:**
**Reasoning:**
**Tradeoff acknowledged:**

## Comment 5 — Sort order
**My position:**
**Reasoning:**
**Engagement with reviewer's point:**

## Comment 6 — Rebase
**What conflicted:**
**How I resolved it:**
**How I verified no conflict remains:**

## PR Description
<!-- Written at the end — feature overview, design decisions, manual testing steps -->