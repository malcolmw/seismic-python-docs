Building network metadata - CSS3.0
==================================

.. toctree::
   :maxdepth: 2
   :caption: Contents:

This tutorial demostrates the basics of building network geometry for a CSS3.0
database (suitable for use with Antelope software).

.. code:: python

   import seispy

   # Instantiate an empty Catalog
   cat = seispy.pandas.catalog.Catalog()
   # Add station PFO to the site table:
   cat.add_row("site",
               dict(sta="PFO", ondate=1982274, lat=33.6117, lon=-116.459, elev=1.259, staname="Pinon Flats Observatory, CA, USA"))
   # Add channel metadata for station PFO to the sitechan table:
   for chan, hang, vang in (("HHZ", 0, 0), ("HHN", 0, 90), ("HHE", 90, 90)):
       cat.add_row("sitechan",
                   dict(sta="PFO", chan=chan, ondate=1982274, edepth=0.005, hang=hang, vang=vang))
   # Add station BALD to the site table:
   cat.add_row("site",
               dict(sta="BALD", ondate=2012268, offdate=2018365, lat=33.6811, lon=-116.742, elev=1.57, staname="Baldy Mountain, CA, USA"))
   # Add channel metadata for station BALD to the sitechan table:
   for chan, hang, vang in (("EHZ", 0, 0), ("HHN", 0, 90), ("HHE", 90, 90)):
       cat.add_row("sitechan",
                   dict(sta="BALD", chan=chan, ondate=2012268, offdate=2018365, edepth=0.007, hang=hang, vang=vang))
   # Write CSS3.0 format database files to disk:
   cat.write("/path/to/output/db")
