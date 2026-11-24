# Functional specification

## Dashboard

Default to today, with date navigation. Show latest weight, change from 90 kg baseline, progress towards 85 kg, latest waist measurement, actual calories and protein versus targets, last night's sleep and seven-day average, today's activity completion and prepared meal stock. Show missing data as not logged, never zero. Show today's scheduled activities, next Oztag session and low-stock warnings. Quick actions: log weight, food/drink, sleep, complete routine, journal. Dashboard and Progress use the same records.

## Meals

Display breakfast, lunch, snack and dinner seeded from the plan. Confirm eaten, undo or edit actual portion. Planned and eaten are distinct. Batch preparation adds portions to inventory without adding calories. Consuming a stocked meal deducts one portion (or actual fraction); allow consumption without stock and flag discrepancy, never negative inventory. Undo reverses associated deduction exactly once. Manual stock adjustment requires quantity and optional reason. Show prepared date, storage type (fridge/freezer) and optional use-by date; never assume food is safe. Low-stock threshold configurable per meal. Generate shopping list from planned portions for selected days, not from assumed pantry inventory. Quick-add snacks/drinks with name, serving, calories and optional protein; save favourites including regular Coke (approx 158 kcal per 375 mL) and Coke Zero (label value). Allow custom foods and manual nutrition estimates. Do not count planned or prepped meals as consumed. Portion scaling uses stored base serving. No automatic exercise calorie credits.

## Weight

Log kg and optional waist cm with date/time. Edit/delete entries. Show latest value, baseline change, goal progress, raw trend and rolling average. No invented values or weight forecasts. Optional weekly waist reminder.

## Sleep

Log bedtime and wake date/time, optional sleep latency and awake minutes, naps with start/end, quality and energy 1--5, notes. Overnight intervals cross midnight correctly. Attribute main sleep to wake date; naps to local start date. Show main sleep separately from naps and total. Target 9:30 pm bedtime, editable wake time and sleep target (initial 8 hours, adjustable). Wednesday late Oztag is a planned exception, not a failure. Do not infer sleep from bedtime alone.

## Progress

Generate scheduled tasks from active plan: daily morning 10 min, lunch 5 min, night 10 min; Monday and Saturday home workout; Tuesday walk, Wednesday Oztag, Thursday recovery walk, Friday optional rest/walk, Sunday walk. Exact exercise details and durations from source plan. Support pending, completed, modified and skipped; optional notes and actual minutes/reps. Complete entire routine or individual steps; allow undo. Optional activities and rest do not penalise adherence. No overdue carry-forward. Show daily and weekly history. Wednesday game time editable per occurrence (7--9:30 pm start, 40 min game plus warm-up). Late games permit shortened night routine and bedtime exception. No automatic increase in exercise intensity; user chooses progression.

## Journal

One editable entry per local calendar day. Date picker and previous/next day, today shortcut. Plain text, optional mood, energy, soreness, hunger and motivation ratings. Autosave with visible saved/error state. No infinite feed. Optional ratings are not required to save.

## Profile

Editable age, sex, height, baseline and goal weight, occupation, availability, goals and personal commitments. Seed male, 31, 175 cm, 90 kg, 85 kg, office work, after 8:30 pm, bed 9:30 pm. Goals: reduce abdominal fat, improve mobility and recovery. Commitments: replace regular Coke, portion rice/potatoes, walk, daily mobility, protect sleep. Display current weight from logs, not a separate conflicting field. Link targets to Settings.

## Settings

Edit meal templates and nutrition, workout and exercise steps, stretches, walking, weekly schedule, sleep targets, game time, inventory thresholds, optional reminders. Seed calorie target 2000 and protein range 130--150 g. Plan changes effective tomorrow by default, optionally today for pending items only. Never change completed historical records. Provide plan preview before applying edits. Import Markdown as a reviewed draft (manual structured editing is acceptable; no AI service required). JSON export/import and reset with explicit confirmation. Optional notifications only if supported and permission granted. No health diagnoses or automated medical advice. Include original plan's recovery cautions.