# Implementation and acceptance tests

## Stage 1 --- Foundation

Set up navigation, responsive monochrome layout, IndexedDB, schema migrations, timezone helpers and seed plan. Convert all meal and routine tables in HEALTH_FITNESS_PLAN.md into structured templates, including exact stretch instructions, workout progression and fallback. Verify totals and preserve source estimates. Seed once only. No demo logs.

## Stage 2 --- Daily operation

Implement dashboard, daily task generation, progress completion/undo, meals and extras, batch stock ledger and shopping list. Add weight and sleep entry. All controls must work and persist across reloads.

## Stage 3 --- Editing and history

Implement settings, profile, date-based journal, history charts, game overrides and backup/import. Add optional reminders only if platform supports them. PWA install/offline support where available. Do not require cloud services.

## Acceptance tests

-   Fresh install displays correct plan, no invented history; reload does not duplicate templates or tasks.
-   Monday/Saturday show home workout; Wednesday shows Oztag; Thursday recovery; daily stretches appear with correct durations. Friday rest/optional walk is not penalised.
-   Confirming a routine updates dashboard and progress; undo restores pending state. Modified/skipped remain distinct. Yesterday's tasks never carry forward.
-   Preparing four meals increases stock by four and adds no calories. Eating one decreases stock by one and adds correct nutrition; repeated taps do not duplicate; undo restores stock and totals. Extra Coke adds calories; Coke Zero uses configured label value.
-   Editing portions recalculates actual nutrition and stock correctly; no negative inventory. Shopping list scales to chosen days.
-   Weight entry persists, trend uses real data, edits/deletes recalculate. Missing weight is not zero.
-   Sleep 23:30 to 07:30 next day gives eight hours before adjustments. Nap remains separate. Test Sydney daylight saving transitions. Late Wednesday game permits bedtime exception.
-   Journal entries on two dates remain separate and persist after reload; autosave errors are visible.
-   Editing tomorrow's meal or routine does not change yesterday's logs or completed tasks. Current-day edits affect pending items only when explicitly chosen.
-   Export, reset and reimport restores all records; invalid import does not overwrite data.
-   App works at narrow phone width, accessible controls, no horizontal overflow, no external tracking. Offline use works after initial load if PWA enabled.

## Definition of done

All required pages functional, persistence verified, calculations tested, no placeholder buttons or fake data. Provide concise run/install instructions and note any unsupported platform features. Keep scope single-user and simple.