# Data model and business rules

Use IndexedDB with schema version and migrations. Stable UUIDs, createdAt/updatedAt timestamps, local date keys YYYY-MM-DD in Australia/Sydney. Store instants as ISO timestamps with timezone conversion. Use transactions for coupled changes. Suggested entities:

  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  Entity                              Fields
  ----------------------------------- ----------------------------------------------------------------------------------------------------------------------------------------------
  Profile                             id, age, sex, heightCm, baselineKg, goalKg, occupation, availability, goals, commitments

  PlanVersion                         id, effectiveDate, targets, mealTemplates, routineTemplates, weeklySchedule, sleepPlan, gameDefaults

  MealTemplate                        id, name, mealSlot, ingredients, baseServing, kcal, proteinG nullable, tracksStock, lowStockThreshold

  RoutineTemplate                     id, name, category, durationMin, steps\[{id,name,instructions,sets,reps,seconds}\], optional

  DailyTask                           id, date, planVersionId, templateSnapshot, status, stepStatuses, actualMinutes, notes, completedAt

  FoodLog                             id, date, timestamp, mealSlot nullable, plannedMealId nullable, foodSnapshot, servings, kcal, proteinG nullable, stockTransactionId nullable

  InventoryBatch                      id, mealTemplateId, preparedAt, storageType, useBy nullable

  StockTransaction                    id, batchId, signedQuantity, reason, foodLogId nullable, timestamp, reversalOf nullable

  Measurement                         id, timestamp, date, weightKg nullable, waistCm nullable

  SleepLog                            id, type main/nap, startAt, endAt, latencyMin nullable, awakeMin nullable, quality nullable, energy nullable, notes

  Journal                             date unique, text, optionalRatings, updatedAt

  GameOverride                        date unique, startTime, durationMin, cancelled, bedtimeException

  FavouriteFood                       id, name, servingLabel, kcal, proteinG nullable
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## Rules

Daily task and planned meal IDs must be deterministic or uniquely constrained by date and scheduled occurrence; generation is idempotent on app open and date change. Snapshot plan values on generation. Historical days use the plan effective on that date. Do not create false completion or consumption records. One planned meal confirmation per occurrence; extras are independent. Stock ledger balance is sum of transactions; use oldest eligible batch first, with manual override. Atomic food log and stock update; editing/deleting reverses original stock effect and applies new effect once. Prevent negative stock. Expired batches are not auto-consumed.

Calories = sum actual food log kcal for selected day. Protein = sum known values; mark incomplete when unknown. Weight change = baseline minus latest measured weight. Goal progress = (baseline-current)/(baseline-goal) when denominator nonzero; clamp visual bar only. Rolling weight average = mean of latest measurement per day over trailing seven calendar days with data; show sample count. Sleep duration = end minus start minus known latency/awake minutes; mark estimated if missing. Reject invalid/overlapping intervals or request correction. Average main sleep over logged nights in trailing seven days; show sample count. Adherence = completed required tasks / scheduled required tasks; display modified separately and optionally report completed-or-modified rate. Exclude optional/rest tasks; no denominator means not applicable. Current day pending tasks are not historical failures.

Validate positive measurements, nonnegative nutrition, finite numeric values, valid dates and serving quantities. Allow zero-calorie drinks. Store historical nutrition and task snapshots independently of templates. JSON backup includes schemaVersion, exportedAt and all entities. Validate imports before replacing data; preview counts and require confirmation. Offer backup before reset. Local storage is device-specific; do not promise sync or encryption. No external analytics or health data transmission.