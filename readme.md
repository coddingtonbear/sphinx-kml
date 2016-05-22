# Sphinx-KML

Embed maps in your restructuredText documents using locally-stored KML files.

## Installation

Install from pip --

```
pip install sphinx-kml
```

Make the following alterations to your Sphinx project's `conf.py`:

* Add `sphinx_kml` to your `extensions` list.
* Set `google_api_key` to a valid Google browser API key.  This will be
  needed for rendering these maps using Google Maps.
* Adding the following two files (from https://code.google.com/archive/p/kmlmapparser/)
  to your project's static assets:
  * https://storage.googleapis.com/google-code-archive-downloads/v2/code.google.com/kmlmapparser/KmlMapParser_packed.css
  * https://storage.googleapis.com/google-code-archive-downloads/v2/code.google.com/kmlmapparser/KmlMapParser.js

```
extensions = [
    # other extensions
    'sphinx_kml',
]
google_api_key = 'MYGOOGLEAPIKEY'
# Assuming you copied the aforementioned kmlmapparser files to the 'static/'
# directory in your project:
html_static_path = ['static/', ]
```

## Basic Use

Just use the `kml` directive with the relative path to a KML file you would
like to render; assuming you have put a file named `some_kml_file.kml` in
the `resources/` subdirectory:

```
.. kml:: resources/some_kml_file.kml
```

## Options

You can also set the following options to customize the display of your KML
map:

* `center`: (Default: center of your provided KML file's contents) If you
  would like to set a different center point, you can provide a
  floating-point latitude and longitude (separated by a space).
* `height`: (Default: 500) The pixel height of the generated map.
* `type`: (Default: 'satellite'; default can be overridden by setting the
  `default_map_type` configuration setting) Map type to display.  Options
  include 'satellite', 'roadmap', 'hybrid', and 'terrain'.
* `zoom`: (Default: a zoom level capable of displaying all KLM points) If
  you would like to set a different zoom level, use this.
* `zoomonclick`: (Default: true) Whether clicking on a displayed point should
  zoom-in on the point.

## Example

```
.. kml:: resources/echolink.kml
   :center: 44.739346 -124.057617
   :zoom: 8
   :zoomonclick: false
```
