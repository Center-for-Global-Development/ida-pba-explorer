# Event Tracking: IDA Allocation Formula Explorer

`interactive_name`: `ida-pba-explorer`

Tracking implemented per the CGD Interactive Analytics Tracking Standard (`analytics-tracking-standard.md` in the CGD interactive toolkit).

`interactive_view` fires once, after the data has loaded.

## Tracked Events

| `action_type` | `action_label` | `action_value` | Notes |
|---|---|---|---|
| `navigate` | `section_tab` | `change_formula`, `change_country` | Tab switch |
| `filter` | `gni_exponent_slider` | slider value (−1 to −0.125, step 0.025) | Fires on `change` |
| `filter` | `cpr_exponent_slider` | slider value (1 to 4, step 0.1) | Fires on `change` |
| `filter` | `base_allocation_slider` | slider value (0 to 50) | Fires on `change` |
| `filter` | `gni_cutoff_slider` | cutoff in US$ (1,000 to 12,000 in steps of 250, plus 1,365) | Fires on `change` |
| `filter` | `gni_cutoff_toggle` | `on`, `off` | |
| `filter` | `poverty_line_select` | poverty line, e.g. `3` | Only shown if more than one line is in the data |
| `preset` | `scenario_preset` | `fy25`, `double_gni_exponent`, `double_gni_exponent_off`, `ida_income_threshold`, `ida_income_threshold_off` | Scenario buttons. `fy25` resets all controls. The other two are toggles that change only their own control (GNI exponent to −0.25; cutoff on at $1,365); `_off` values are sent when a pressed button is clicked to turn it off |
| `view_control` | `scatter_x_axis` | `gnipc`, `cpr`, `pov` | |
| `view_control` | `change_metric` | `pct`, `abs` | |
| `view_control` | `table_sort` | column key (`country`, `gnipc`, `cpr`, `pov`, `base`, `now`, `abs`, `pct`) | |
| `download` | `results_csv` | | CSV of the country table |
| `filter` | `country_select` | country name (74 values) | Tab 2 |
| `filter` | `change_variable` | `gni`, `cpr` | Tab 2 |
| `filter` | `formula_basis` | `fy25`, `mine` | Tab 2 |
| `filter` | `gni_multiplier_slider` | multiplier: 1 d.p. below 10 (0.3 to 9.9), whole numbers from 10 to 20 (about 110 values) | Tab 2, fires on `change` |
| `filter` | `cpr_change_slider` | CPR change, rounded to 1 d.p. (−1.5 to 1.5, 31 values) | Tab 2, fires on `change` |
| `preset` | `reset_country_change` | | Tab 2: sets GNI multiplier to x1 and CPR change to 0 |
| `preset` | `country_scenario` | `ghana_new_zealand`, `ghana_8x`, `afdb_cpia_gap`, each also with `_off` | Tab 2 scenario buttons from the blog post. `_off` is sent when a pressed button is clicked, which resets to no change |

## Not Tracked

- **Chart hover and tooltips:** high volume, low signal.
- **Slider drag (`input` events):** only the final `change` value is sent.
