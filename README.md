Danish Polls
============
[![MIT-license badge](https://img.shields.io/badge/License-MIT-blue.svg)][license]
[![CSV-validation badge](http://csvlint.io/validation/540d77206373766b9d0f0000.svg?revalidate=false)][csv-validation]
[![Download link](https://img.shields.io/badge/Download-Link-ff69b4.svg)][download]

Updating the data on the [relevant wiki][wiki] is becoming a royal pain, so I might as well update the polling data here, in a CSV file. This will also speed up the process of updating interactive graphics reliant on the data.

- View the data [here][view].
- Download the project as a compressed file [here][download].
- Get the raw CSV [here][raw].

More polls can be found using [this collection of polls][collection].

## Displaying the Data with D3 ##
I am *still* trying to figure out how to plot a LOESS trendline in JavaScript with [science.js][science.js] to finish up my [Party Trend chart][party-trend], so *any* [help][issue] towards achieving that would be appreciated immensely.

## Spreadsheet Data ##
As mentioned, the data was retrieved from the [wiki][wiki] with the latest Danish opinion polling—which I contributed to myself—using Google Docs. For more on how I did that, see [this guide][docs-guide].

That guide does not mention how to clean the sorry raw data you get in Google Spreadsheets, so here are the steps for cleaning the data, after you’ve saved it as, say, a CSV file.

### Cleaning Spreadsheet Data ###
1. Remove header separator (`,,,`).
2. Put all headers on one line.
3. Remove all footnotes (`[1]`, `[2]`, etc.).
4. Fix the non-2014 year dates shown as 2014.
5. Remove all year separator lines (`2014,,,`).
6. Remove the line with the `EP election`.
7. (Optional: Remove all YouGov polls.)


[license]: https://github.com/ndarville/danish-polls/blob/master/LICENSE.md
[download]: https://github.com/ndarville/danish-polls/archive/master.zip
[csv-validation]: http://csvlint.io/validation/540d77206373766b9d0f0000
[wiki]: https://en.wikipedia.org/wiki/Opinion_polling_for_the_next_Danish_general_election
[view]: https://github.com/ndarville/danish-polls/blob/master/data.csv
[raw]: https://raw.githubusercontent.com/ndarville/danish-polls/master/data.csv
[collection]: https://github.com/ndarville/d3-charts/tree/master/_data
[d3-charts]: https://github.com/ndarville/d3-charts
[science.js]: https://github.com/jasondavies/science.js/
[party-trend]: http://bl.ocks.org/ndarville/11094667
[issue]: https://github.com/ndarville/d3-charts/issues/5#issuecomment-46226887
[docs-guide]: https://github.com/ndarville/d3-charts/tree/master/_data/denmark
