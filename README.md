
# Simple scripts for POIs on the Skoda Columbus2 and Amundsen SatNavs

The skoda destinations website can be used to build a POI database for the Skoda
Columbus and Amundsen SatNavs. However, it currently does not compute the checksums
correctly so cannot be loaded onto the SatNav. It is also quite unreliable.

These scripts can be used to:
  - Correct the checksums of an existing POI database
  - Build the POI database without using the Skoda Destinations website

This should work on all versions of python 2.7 onwards, and run on Windows, Mac and Linux.

The following issues may be encountered:
  - Only csv data is currently supported
  - Non utf-8 characters may not work (untested)
  - Only tested with 39x39 png icons


## Fixing the checksums using poifix

```
# For Amundsen
python /path/to/poifix.py /path/to/MIB2TSD

# For Columbus
python /path/to/poifix.py /path/to/MIB2HIGH
```

## Building a new POI database

The mypois.py script needs a configuration file. By default it will use config.ini in the same directory as the script.

```
# Using config.ini
python /path/to/mypois.py

# Using your own configuration script
python /path/to/mypois.py /path/to/config.ini
```

An (annotated) example configuration file
```
[General]
OutputDirectory=mydir                 # The name of the output directory (must not exist)

[traffic]                             # One section per category
Name=GB Traffic Light Cameras         # The category name
Warning=True                          # Use 'True' to get a sound notification when near
Source=../GBFeuRougeGB.csv            # The input file containing the POIs **Currently only csv files are supported**
Icon=../traffic.png                   # The icon to use                    **Currently only 39x39 icons are supported**
Disabled=False                        # Optional element, set to True if you want this section to be skipped

[variable]                            # Another section
Name=GB Variable Speed Cameras
Warning=True
Source=../variable_speed.csv
Icon=../variable.png
```
