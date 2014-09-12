Tests for CSV Data
==================
This is a quick to I developed for detecting bad entries, which is to be expected, when you manually enter a truckload of polls.

The script currently tests two things:

1. That the combined vote share for the coalition parties matches number in their corresponding coalition column.
2. That the lead (i.e. difference between the two biggest parties) matches the numbers in the `Lead` column.

You can use it like this:

1. Download entire project, not just the `_tests` folder to your computer.
2. In your terminal, go to the root folder, i.e. one step above `_tests`.
3. Run `python -m SimpleHTTPServer 8000` in your terminal.
4. Go to `localhost:8000/_tests/` in your favourite browser.
5. The rest should follow from here.

For more behind the scenes, go [here][issue].


[issue]: https://github.com/ndarville/danish-polls/issues/1
