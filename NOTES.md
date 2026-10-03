# Patch Notes

## Summary

I fixed three focused issues in the task search and frontend filtering flow.

1. Fixed the SQL search query by grouping the title/description conditions so the archived and status filters apply to the complete search.
2. Reset pagination to page 1 whenever the search or status filter changes.
3. Fixed stale frontend error state by clearing errors after a successful request and stopping the loading state when a request fails.

I verified the SQL issue using API requests before and after the fix, tested filter pagination through the UI, and verified error recovery. Backend tests and the frontend production build both pass.

## What I Did Not Change

I did not rewrite the repository/controller structure or add a service layer because the assignment requested a focused patch. I also did not change the artificial query delay, database pagination approach, or startup warnings because these require broader design decisions and were not necessary to address the reproduced user-facing issues.

## Biggest Remaining Risk

Pagination is still performed in memory after loading all matching tasks from the database. This may become inefficient as the task table grows significantly.

## AI / Tools Used

Used ChatGPT for code review, debugging guidance, explaining SQL operator precedence, and reviewing the focused changes. Used the terminal, curl, Maven, npm/Vite, and browser testing to reproduce and verify the issues.
