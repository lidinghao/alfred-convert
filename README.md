
Alfred-Convert
==============

Convert between different units offline in [Alfred 2 & 3][alfred].

![][demo]

Alfred-Convert uses a [built-in library][pintdocs] for lightning-fast conversions.

You can also add your own custom units.

**Note:** Currency conversions do require occasional Internet connectivity to update exchange rates. Alfred-Convert will otherwise work just fine without an Internet connection.

- [Downloading](#downloading)
- [Usage](#usage)
    - [Conversions](#conversions)
    - [Configuration](#configuration)
    - [Active currencies](#active-currencies)
    - [Custom units](#custom-units)
- [Supported units](#supported-units)
    - [Supported currencies](#supported-currencies)
    - [Adding custom units](#adding-custom-units)
- [Releases](#releases)
- [Thanks, copyright, licensing](#thanks-copyright-licensing)


Downloading
-----------

Download from [GitHub releases][ghreleases].

**Note**: Version 3.0 and above only supports Alfred 3. If you're still using Alfred 2, please download [v2.6][v2.6].


Usage
-----

- `conv <quantity> <from unit> [<to unit>]` — Perform a conversion
    - `↩` or `⌘C` — Copy the result to the pasteboard
    - `⌘↩` — Add/remove destination unit as default for this dimensionality
    - `⌘L` — Show result in Alfred's Large Type window
- `convinfo` — View help file and information about the workflow, or edit custom units and active currencies
    - `View Help File` — Open this page in your browser
    - `View All Supported Currencies` — View/filter the list of all supported currencies in Alfred
    - `Edit Active Currencies` — Edit the list of active currencies in your default text editor
    - `Edit Custom Units` — Edit the list of custom currencies in your default text editor


### Conversions ###

- `conv <quantity> <from unit> [<to unit>]` — Perform a conversion
    - `↩` or `⌘C` — Copy the result to the pasteboard
    - `⌘↩` — Add/remove destination unit as default for this dimensionality
    - `⌘L` — Show result in Alfred's Large Type window

If no destination unit is specified, any defaults you've saved will be used (that aren't the same as the source unit).

The syntax is simple: the quantity, the unit you want to convert from then (optionally) the unit you want to convert to. For example:

- `conv 128 mph kph`
- `conv 72in cm`
- `conv 100psi bar`
- `conv 20.5 m/s mph`
- `conv 100 eur gbp`

It doesn't matter if there is a space between the quantity and the units or not. Alfred-Convert will tell you if it doesn't understand your query or know the units.

Actioning an item (selecting it and hitting `↩`) will copy it to the clipboard. Using `⌘+L` will display the result in Alfred's large text window, `⌘+C` will copy the selected result to the clipboard.


### Configuration ###

The workflow is configured via the configuration sheet (`[𝓍]`) in Alfred Preferences and via a couple of text files in its data directory.


#### Configuration sheet ####

Basic configuration is performed in the configuration sheet:

|         Option        |                                           Meaning                                            |
|-----------------------|----------------------------------------------------------------------------------------------|
| `COPY_UNIT`           | Include unit when copying conversion result. Any value but `0` or empty turns this option on |
| `DECIMAL_PLACES`      | Number of decimal places to show in results                                                  |
| `DECIMAL_SEPARATOR`   | Character to separate whole numbers and decimal fractions                                    |
| `THOUSANDS_SEPARATOR` | Character to delimit thousands                                                               |
| `UPDATE_INTERVAL`     | How often (in minutes) to update currency exchange rates                                     |


#### Active currencies ####

By default, all supported fiat currencies and a handful of the most popular cryptocurrencies are active.

- `convinfo`
    - `View All Supported Currencies`
    - `Edit Active Currencies`

Use `Edit Active Currencies` to open the list of active currencies in your default editor. Add the symbol for the currency you'd like to activate on a new line in this file.

You can use `View All Supported Currencies` to search for the currency you'd like to activate, then use `⌘C` on the result to copy the symbol to the pasteboard.


#### Custom units ####

See [Adding custom units](#adding-custom-units).


Supported units
---------------

Currently, Alfred-Convert only supports [the units][pintunits] understood by the underlying [Pint][pintdocs] library plus [currencies](#supported-currencies) and a handful of additional units.

You can [add your own custom units](#adding-custom-units) to the workflow. If you think they'd be useful to everyone, please create a corresponding [GitHub issue][ghissues] to request addition as a default unit or submit a [pull request][ghpulls].


### Supported currencies ###

To convert, use the appropriate **abbreviation** for the relevant currencies, e.g. `conv 100 eur gbp`.

You can also view (and search) the list from within Alfred by using the keyword `convinfo` and choosing `View All Supported Currencies`.

[All supported currencies](./docs/currencies.md).


### Adding custom units ###

You can add your own custom units using the [format defined by Pint][pinthowto]. Add your definitions to the `unit_definitions.txt` file in the workflow's data directory.

To edit this file, enter `convinfo` in Alfred and select `Edit Custom Units`. The `unit_definitions.txt` file will open in your default text editor.

Please see the [Pint documentation][pinthowto] for the required format. See Pint's [default unit definitions][pintunits] for examples.


Releases
--------

See [CHANGELOG][changelog] for more information.

|   Release   |      Date      |
|-------------|----------------|
| [3.0][v3.0] | 2017-07-16     |
| [2.6][v2.6] | 2017-06-15     |
| [2.5][v2.5] | 2015-12-11     |
| [2.4][v2.4] | 2015-11-28     |
| [2.3][v2.3] | 2015-11-26     |
| [2.2][v2.2] | 2015-07-16     |
| 2.1         | Never released |
| [2.0][v2.0] | 2014-12-26     |
| [1.2][v1.2] | 2014-08-19     |
| [1.1][v1.1] | 2014-08-09     |


Thanks, copyright, licensing
----------------------------

- The Python [Pint][pintdocs] library does all the heavy lifting. See the [Pint GitHub repo][pintrepo] for Pint licensing or `LICENSE.txt` and `AUTHORS.txt` in the `vendor/pint` subdirectory.
- The workflow icons are from [Font Awesome][fontawesome]
- Exchange rates are downloaded from [Yahoo! Finance][yahoo-finance] and [CryptoCompare][cryptocompare] (for cryptocurrencies).
- The [Alfred-Workflow][alfred-workflow] library is used heavily.

All other code/media are released under the [MIT Licence][mit].


[alfred-workflow]: http://www.deanishe.net/alfred-workflow/
[alfred]: http://www.alfredapp.com/
[changelog]: ./CHANGELOG.md
[demo]: https://raw.github.com/deanishe/alfred-convert/master/demo.gif
[fontawesome]: http://fortawesome.github.io/Font-Awesome/
[ghissues]: https://github.com/deanishe/alfred-convert/issues
[ghpulls]: https://github.com/deanishe/alfred-convert/pulls
[ghreleases]: https://github.com/deanishe/alfred-convert/releases
[mit]: http://opensource.org/licenses/MIT
[pintdocs]: http://pint.readthedocs.org/en/latest/index.html
[pinthowto]: http://pint.readthedocs.org/en/latest/defining.html
[pintrepo]: https://github.com/hgrecco/pint
[pintunits]: https://github.com/hgrecco/pint/blob/master/pint/default_en.txt
[v1.1]: https://github.com/deanishe/alfred-convert/releases/tag/v1.1
[v1.2]: https://github.com/deanishe/alfred-convert/releases/tag/v1.2
[v2.0]: https://github.com/deanishe/alfred-convert/releases/tag/v2.0
[v2.2.1]: https://github.com/deanishe/alfred-convert/releases/tag/v2.2.1
[v2.2]: https://github.com/deanishe/alfred-convert/releases/tag/v2.2
[v2.3]: https://github.com/deanishe/alfred-convert/releases/tag/v2.3
[v2.4]: https://github.com/deanishe/alfred-convert/releases/tag/v2.4
[v2.5]: https://github.com/deanishe/alfred-convert/releases/tag/v2.5
[v2.6]: https://github.com/deanishe/alfred-convert/releases/tag/v2.6
[v3.0]: https://github.com/deanishe/alfred-convert/releases/tag/v3.0
[yahoo-finance]: https://finance.yahoo.com/
[cryptocompare]: https://www.cryptocompare.com/
