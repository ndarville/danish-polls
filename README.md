Danish Polls
============
[![MIT-license badge](https://img.shields.io/badge/License-MIT-blue.svg)][license]
[![Download link](https://img.shields.io/badge/Download-Link-ff69b4.svg)][download]

[![Opinion-poll chart][chart-img]][d3-charts]

Updating the data on the [relevant wiki][wiki] is becoming a royal pain, so I might as well update the polling data here, in a CSV file. This will also speed up the process of updating interactive graphics reliant on the data.

- View and inspect the data [here][view].
- Download the project as a compressed file [here][download].
- Get the raw CSV [here][raw].

More polls can be found using [this collection of polls][collection].

Because manually entering data inevitably results in human errors, I have created a basic [test script][tests] that detects inconsistencies in how the individual values match calculations based on those figures. The findings of this script that have not been addressed are available in the `INCONSISTENCIES.md` file, available [here][inconsistencies].s

## Understanding the Data ##

### Table Excerpt ###

 Polling Firm | Date      | V    | A    | O    | B   | F   | Ø   | I   | C   | K   | Lead | Red (A+B+F+Ø) | Blue (V+O+I+C+K)
:-------------|----------:|-----:|-----:|-----:|----:|----:|----:|----:|----:|----:|-----:|--------------:|-----------------:
 Voxmeter     | 9/14/2014 | 25.9 | 22.7 | 17.7 | 7.2 | 7.2 | 8.3 | 5.3 | 4.8 | 0.4 | 3.2  | 45.4          | 54.1
 Gallup       | 9/11/2014 | 22.5 | 21.7 | 18.5 | 9.1 | 6.2 | 9.8 | 6.2 | 5.2 | 0.4 | 0.8  | 46.8          | 52.8
 Wilke        |  9/7/2014 | 24.4 | 22.4 | 18.9 | 8.7 | 7.2 | 7.9 | 4.5 | 5.0 | 1.0 | 2.0  | 46.2          | 53.8

### Table Legend ####

 Column(s)        | Description                                                          | Value Type
:-----------------|:---------------------------------------------------------------------|:---------------------------
 Polling Firm     | Firm behind the opinion poll.                                        | Text
 Date             | Date of opinion poll.                                                | Date: `MM/DD/YY`/`%m/%d/%Y`
 V, O, I, C, K    | Parties in right (“blue”) coalition. (*Provided.*)                   | Per cent: `0.0–100.0`
 A, B, F, Ø       | Parties in left (“red”) coalition. (*Provided.*)                     | -
 Lead             | Difference between the two biggest parties. (*Manually calculated.*) | -
 Red (A+B+F+Ø)    | Total of party vote share in red coalition. (*Provided.*)            | -
 Blue (V+O+I+C+K) | Total of party vote share in blue coalition. (*Provided.*)           | -

## Displaying the Data with D3 ##
I am *still* trying to figure out how to plot a LOESS trendline in JavaScript with [science.js][science.js] to finish up my [Party Trend chart][party-trend], so *any* [help][issue] towards achieving that would be appreciated immensely.

You can see the status of the fancy chart at the top of this project page.

## Additional Polling Data ##

### `all-polls.csv` ###
Polling companies like YouGov do some dreadful polling, but some people still want to use their data towards their own ends. Because of this, I have included the YouGov data in the file called [`all-polls.csv`][all-polls].

### 2011-Election Data ###
To find out more, go to [its folder][2011].

## Spreadsheet Data ##
As mentioned, the data was retrieved from the [wiki][wiki] with the latest Danish opinion polling—which I contributed to myself—collated using various poll aggregators. The wiki data is then imported using Google Docs. For more on how I did that, see [this guide][docs-guide].

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
[science.js]: https://github.com/jasondavies/science.js/
[party-trend]: http://bl.ocks.org/ndarville/11094667
[issue]: https://github.com/ndarville/d3-charts/issues/5#issuecomment-46226887
[docs-guide]: https://github.com/ndarville/d3-charts/tree/master/_data/denmark
[issues]: https://github.com/ndarville/danish-polls/issues
[swe-polls]: https://github.com/MansMeg/SwedishPolls
