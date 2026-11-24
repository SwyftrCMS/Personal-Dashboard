# Interface and navigation

Mobile-first, black/white/grey only, system font, simple borders, no gradients, shadows, decorative imagery or animation. Accessible contrast, labelled controls, keyboard support, minimum 44px touch targets. Responsive desktop layout. Use text plus icons; never rely on colour alone for status.

Bottom navigation: Dashboard \| Meals \| Weight \| Sleep \| Progress. Header menu: Journal \| Profile \| Settings. Keep current date visible on daily pages; previous/next and today controls. Date picker for historical access. Preserve selected date when switching daily pages.

## Screen hierarchy

  ------------------------------------------------------------------------------------------------------------------------------------
  Page              Top                             Main                                    Secondary
  ----------------- ------------------------------- --------------------------------------- ------------------------------------------
  Dashboard         Date and quick actions          KPI grid and today's checklist          Stock alerts and upcoming game

  Meals             Actual calorie/protein totals   Planned meal rows with eaten buttons    Extras, stock, batch prep, shopping list

  Weight            Latest weight and log button    Trend chart                             Waist and editable history

  Sleep             Last sleep and log button       Main sleep and nap entries              Weekly averages

  Progress          Date and completion count       Morning/lunch/activity/night sections   Weekly calendar

  Journal           Date selector                   Text editor                             Optional ratings and save state

  Profile           Goals                           Personal details                        Commitments

  Settings          Plan sections                   Editable templates                      Backup and import
  ------------------------------------------------------------------------------------------------------------------------------------

Use compact forms with sensible defaults, numeric keyboards for quantities and units next to inputs. One-tap completion with undo; edit details only when necessary. Show explicit empty states, errors and loading states. Confirm destructive actions. Charts should have text summaries and distinguish missing observations from zero. Avoid streaks, guilt language and competitive scoring. No fictional metrics on first launch.