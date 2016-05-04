# Feed-Read-Parser

[Node.js](http://nodejs.org/) module for parsing RSS and ATOM feeds into
a common article object.

This module is forked from [feed-read](https://www.npmjs.com/package/feed-read) npm module. It aims to fix old bugs in the forked version.

# Installation

    $ npm install feed-read-parser

# Usage

    var feed = require("feed-read-parser");

## `feed(url, callback)`
Fetch a feed.

    feed("http://craphound.com/?feed=rss2", function(err, articles) {
      if (err) throw err;
      // Each article has the following properties:
      //
      //   * "title"     - The article title (String).
      //   * "author"    - The author's name (String).
      //   * "link"      - The original article link (String).
      //   * "content"   - The HTML content of the article (String).
      //   * "published" - The date that the article was published (Date).
      //   * "feed"      - {name, source, link}
      //
    });

## `feed(array, callback)`
Fetch several feeds thanks to a given array

    var rss = [
      'http://www.eurogamer.net/?format=rss',
      'http://fr.ign.com/feed.xml',
      'http://www.gamekult.com/feeds/actu.html'
    ]

    feed(rss, function(err, articles) {
        if (err) throw err;
        // articles is an array of article with properties described above.
    });

## `feed.rss(rss_string, callback)`
Parse a string of XML as RSS.

The callback receives `(err, articles)`.

## `feed.atom(atom_string, callback)`
Parse a string of XML as ATOM.

The callback receives `(err, articles)`.

## `feed.identify(xml_string)` // => "atom", "rss", or false
Identify what type of feed the XML represents.

Returns `false` when it is neither RSS or ATOM.


# License
See LICENSE.
