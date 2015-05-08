Danish Polls
============
[![Build Status](https://travis-ci.org/ndarville/danish-polls.svg?branch=master)][travis]
[![MIT-license badge](https://img.shields.io/badge/License-MIT-blue.svg)][license]
[![Download link](https://img.shields.io/badge/Download-Link-ff69b4.svg)][download]

[![Opinion-poll chart][chart-img]][d3-charts]

Updating the data on the [relevant wiki][wiki] is becoming a royal pain, so I might as well update the polling data here, in a CSV file. This will also speed up the process of updating interactive graphics reliant on the data.

- View and inspect the data [here][view].
- Download the project as a compressed file [here][download].
- Get the raw CSV [here][raw].

More polls can be found using [this collection of polls][collection].

Because manually entering data inevitably results in human errors, I have created a basic [test script][tests] that detects inconsistencies in how the individual values match calculations based on those figures. The findings of this script that have not been addressed are available in the `INCONSISTENCIES.md` file, available [here][inconsistencies].

## Understanding the Data ##

### Table Excerpt ###

 Polling Firm | Date       | V    | A    | O    | B   | F   | Ø   | I   | C   | K   | Å   | Lead | Red (A+B+F+Ø+Å) | Blue (V+O+I+C+K)
:-------------|-----------:|-----:|-----:|-----:|----:|----:|----:|----:|----:|----:|----:|-----:|----------------:|-----------------:
 Voxmeter     | 2015-03-01 | 22.3 | 23.1 | 19.6 | 7.8 | 6.9 | 8.5 | 4.8 | 5.3 | 0.3 | 1.2 | 0.8  | 47.5            | 52.3
 Epinion      | 2015-02-23 | 23.7 | 22.0 | 21.7 | 6.3 | 6.3 | 8.9 | 5.7 | 4.9 | 0.7 | -   | 1.7  | 43.5            | 56.7
 Voxmeter     | 2015-02-22 | 23.5 | 23.7 | 18.3 | 7.7 | 7.1 | 8.8 | 6.1 | 4.2 | 0.3 | -   | 0.2  | 47.3            | 52.4

### Table Legend ####

 Column(s)        | Description                                                          | Value Type
:-----------------|:---------------------------------------------------------------------|:----------------------------------------
 Polling Firm     | Firm behind the opinion poll.                                        | Text
 Date             | Date of opinion poll.                                                | Date: `YYYY-MM-DD`/`%Y-%m-%d`/[`ISO 8601`][xkcd]
 V, O, I, C, K    | Parties in right (“blue”) coalition. (*Provided.*)                   | Per cent, `0.0–100.0`, or null, `-`
 A, B, F, Ø, Å    | Parties in left (“red”) coalition. (*Provided.*)                     | ibid.
 Lead             | Difference between the two biggest parties. (*Manually calculated.*) | Per cent: 0.0–100.0
 Red (A+B+F+Ø+Å)  | Total of party vote share in red coalition. (*Provided.*)            | Per cent: 0.0–100.0
 Blue (V+O+I+C+K) | Total of party vote share in blue coalition. (*Provided.*)           | Per cent: 0.0–100.0

## Displaying the Data with D3 ##
I am *still* trying to figure out how to plot a LOESS trendline in JavaScript with [science.js][science.js] to finish up my [Party Trend chart][party-trend], so *any* [help][issue] towards achieving that would be appreciated immensely.

You can see the status of the fancy chart at the top of this project page.

## Additional Polling Data ##

### `all-polls.csv` ###
Polling companies like YouGov do some dreadful polling, but some people still want to use their data towards their own ends. Because of this, I have included the YouGov data in the file called [`all-polls.csv`][all-polls].

You convert `all-polls.csv` to `data.csv` with

```sh
$ grep -v YouGov all-polls.csv > data.csv
```

And, if needed, you can sort it with

```sh
$ sort -r -n -t"," -k2.4 -k2.6 -k2.7 -k2.9 -k2.10 all-polls.csv > sorted.csv
# And move the header back to the top afterwards
```

You can probably get away with a general CSV sort, since the date format conforms to the ISO 8601 standard:

```sh
$ sort -t"," -r -k2 all-polls.csv > sorted.csv
```

### 2011-Election Data ###
To find out more, go to [its folder][2011].

## Getting Opinion-Polling Data from Wikis ##
You can retrieve *some* Danish opinion-polling data from the [wiki][wiki]—as well as data from other countries. To achieve this, you can use Google Docs. For more on how I did that, see [this guide][docs-guide].

That guide does not mention how to clean the sorry raw data you get in Google Spreadsheets, so here are the steps for cleaning the data, after you’ve saved it as, say, a CSV file.

### Cleaning Spreadsheet Data ###
1. Remove header separator (`,,,`).
2. Put all headers on one line.
3. Remove all footnotes (`[1]`, `[2]`, etc.).
4. Fix the non-2014 year dates shown as 2014.
5. Remove all year separator lines (`2014,,,`).
6. Remove the line with the `EP election`.
7. (Optional: Remove all YouGov polls.)

### To-Do List ###
Visit the project’s [issue tracker][issues] to follow its status and development. There is still much to be done.

### Sibling Projects ###
- [Swedish Polls][swe-polls]


[travis]: https://travis-ci.org/ndarville/danish-polls
[license]: https://github.com/ndarville/danish-polls/blob/master/LICENSE.md
[download]: https://github.com/ndarville/danish-polls/archive/master.zip
[d3-charts]: https://github.com/ndarville/d3-charts
[chart-img]: https://raw.githubusercontent.com/ndarville/danish-polls/master/chart.png
[wiki]: https://en.wikipedia.org/wiki/Opinion_polling_for_the_next_Danish_general_election
[view]: https://github.com/ndarville/danish-polls/blob/master/data.csv
[raw]: https://raw.githubusercontent.com/ndarville/danish-polls/master/data.csv
[collection]: https://github.com/ndarville/d3-charts/tree/master/_data
[tests]: https://github.com/ndarville/danish-polls/tree/master/_tests
[inconsistencies]: https://github.com/ndarville/danish-polls/blob/master/INCONSISTENCIES.md
[all-polls]: https://github.com/ndarville/danish-polls/blob/master/all-polls.csv
[2011]: https://github.com/ndarville/danish-polls/election2011
[xkcd]: https://xkcd.com/1179/
[science.js]: https://github.com/jasondavies/science.js/
[party-trend]: http://bl.ocks.org/ndarville/11094667
[issue]: https://github.com/ndarville/d3-charts/issues/5#issuecomment-46226887
[docs-guide]: https://github.com/ndarville/d3-charts/tree/master/_data/denmark
[issues]: https://github.com/ndarville/danish-polls/issues
[swe-polls]: https://github.com/MansMeg/SwedishPolls
