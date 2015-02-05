Timeframes provide a shorthand for specifying the query from/to dates. The full representation of a timeframe is:
[block:code]
{
  "codes": [
    {
      "code": "{\n  start: \"2014-02-13T00:00:00.000Z\",\n  end: \"2014-02-13T23:59:59.999Z\"\n}",
      "language": "json"
    }
  ]
}
[/block]
We took the more common timeframes and created a shorthand string for them. There are three main groups of timeframes: `this`, `last` and `previous`:
[block:parameters]
{
  "data": {
    "h-0": "Timeframe",
    "h-1": "Description",
    "0-0": "`this_n_seconds`",
    "1-0": "`this_n_minutes`",
    "2-0": "`this_n_hours`",
    "3-0": "`this_n_days`",
    "4-0": "`this_n_months`",
    "5-0": "`this_n_years`",
    "6-0": "`last_n_seconds`",
    "7-0": "`last_n_minutes`",
    "8-0": "`last_n_hours`",
    "9-0": "`last_n_days`",
    "10-0": "`last_n_months`",
    "11-0": "`last_n_years`",
    "12-0": "`previous_n_seconds`",
    "13-0": "`previous_n_minutes`",
    "14-0": "`previous_n_hours`",
    "15-0": "`previous_n_days`",
    "16-0": "`previous_n_months`",
    "17-0": "`previous_n_years`",
    "0-1": "Creates a timeframe with all of the current second and the previous completed n-1 seconds.",
    "1-1": "Creates a timeframe with all of the current minute and the previous completed n-1 minutes.",
    "2-1": "Creates a timeframe with all of the current hour and the previous completed n-1 hours.",
    "3-1": "Creates a timeframe with all of the current day and the previous completed n-1 days.",
    "4-1": "Creates a timeframe with all of the current month and the previous completed n-1 months.",
    "5-1": "Creates a timeframe with all of the current year and the previous completed n-1 years.",
    "6-1": "Creates a timeframe with the start of `n` seconds before the most recent second and an end at the most recent second.\n\nExample: if right now it is 08:30:43.555 and we use “last_3_seconds”, this will result in a timeframe of 08:30:40 until 08:30:43.",
    "7-1": "Creates a timeframe with the start of `n` minutes before the most recent second and an end at the most recent second.\n\nExample: if right now it is 08:30:43 and we use “last_3_minutes”, this will result in a timeframe of 08:27:43 until 08:30:43.",
    "8-1": "Creates a timeframe with the start of `n` hours before the most recent second and an end at the most recent second.\n\nExample: if right now it is 08:30:43 and we use “last_3_hours”, this will result in a timeframe of 05:30:43 until 08:30:43.",
    "9-1": "Creates a timeframe with the start of `n` days before the most recent second and an end at the most recent second.\n\nExample: if right now it is 2014-02-14 08:30:43 and we use “last_3_days”, this will result in a timeframe of 2014-02-11 08:30:43 until 201-02-14 08:30:43.",
    "10-1": "Creates a timeframe with the start of `n` months before the most recent second and an end at the most recent second.\n\nExample: if right now it is 2014-02-14 08:30:43 and we use “last_3_months”, this will result in a timeframe of 2013-11-14 08:30:43 until 201-02-14 08:30:43.",
    "11-1": "Creates a timeframe with the start of `n` years before the most recent second and an end at the most recent second.\n\nExample: if right now it is 2014-02-14 08:30:43 and we use “last_3_years”, this will result in a timeframe of 2011-02-14 08:30:43 until 201-02-14 08:30:43.",
    "12-1": "Creates a timeframe with the start of `n` seconds before the most recent complete second and an end at the most recent complete second.\n\nExample: if right now it is 08:30:43.555 and we use “previous_3_seconds”, this will result in a timeframe of 08:30:40 until 08:30:43.",
    "13-1": "Creates a timeframe with the start of `n` minutes before the most recent complete minute and an end at the most recent complete minute.\n\nExample: if right now it is 08:30:43 and we use “previous_7_minutes”, this will result in a timeframe of 08:23 until 08:30.",
    "14-1": "Creates a timeframe with the start of `n` hours before the most recent complete hour and an end at the most recent complete hour.\n\nExample: if right now it is 08:30:43 and we use “previous_3_hours”, this will result in a timeframe of 05:00 until 08:00.",
    "15-1": "Creates a timeframe with the start of `n` days before the most recent complete minute and an end at the most recent complete day.\n\nExample: if right now it is 2014-02-14 08:30:43 and we use “previous_7_days”, this will result in a timeframe of 2014-02-07 until 2014-02-14.",
    "16-1": "Creates a timeframe with the start of `n` months before the most recent complete month and an end at the most recent complete month.\n\nExample: if right now it is 2014-02-14 08:30:43 and we use “previous_4_months”, this will result in a timeframe of 2013-10-01 until 2014-02-01.",
    "17-1": "Creates a timeframe with the start of `n` years before the most recent complete year and an end at the most recent complete year.\n\nExample: if right now it is 2014-02-14 08:30:43 and we use “previous_3_years”, this will result in a timeframe of 2011-01-01 until 2014-01-01."
  },
  "cols": 2,
  "rows": 18
}
[/block]
#Synonyms
[block:parameters]
{
  "data": {
    "0-0": "`today`",
    "1-0": "`yesterday`",
    "2-0": "`this_second`",
    "3-0": "`this_minute`",
    "4-0": "`this_hour`",
    "5-0": "`this_day`",
    "6-0": "`this_month`",
    "7-0": "`this_year`",
    "8-0": "`last_second`",
    "9-0": "`last_minute`",
    "10-0": "`last_hour`",
    "11-0": "`last_day`",
    "12-0": "`last_month`",
    "13-0": "`last_year`",
    "14-0": "`previous_second`",
    "15-0": "`previous_minute`",
    "16-0": "`previous_hour`",
    "17-0": "`previous_day`",
    "18-0": "`previous_month`",
    "19-0": "`previous_year`",
    "0-1": "Synonym for `this_day`.",
    "1-1": "Synonym for `previous_1_day`.",
    "2-1": "Synonym for `this_1_second`.",
    "3-1": "Synonym for `this_1_minute`.",
    "4-1": "Synonym for `this_1_hour`.",
    "5-1": "Synonym for `this_1_day`.",
    "6-1": "Synonym for `this_1_month`.",
    "7-1": "Synonym for `this_1_year`.",
    "8-1": "Synonym for `last_1_second`.",
    "9-1": "Synonym for `last_1_minute`.",
    "10-1": "Synonym for `last_1_hour`.",
    "11-1": "Synonym for `last_1_day`.",
    "12-1": "Synonym for `last_1_month`.",
    "13-1": "Synonym for `last_1_year`.",
    "14-1": "Synonym for `previous_1_second`.",
    "15-1": "Synonym for `previous_1_minute`.",
    "16-1": "Synonym for `previous_1_hour`.",
    "17-1": "Synonym for `previous_1_day`.",
    "18-1": "Synonym for `previous_1_month`.",
    "19-1": "Synonym for `previous_1_year`.",
    "h-0": "Synonym",
    "h-1": "Description"
  },
  "cols": 2,
  "rows": 20
}
[/block]