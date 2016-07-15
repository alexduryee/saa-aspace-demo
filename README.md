# ArchivesSpace EAD Plugin Demonstration

## About This Plugin

This plugin modifies the ArchivesSpace EAD output to include a new attribute, `type="local_mss"`, in `<unitid>` elements.

Created by Alex Duryee as a demonstration of the "Making ArchivesSpace Work for You" presentation at the 2016 annual meeting of the Society of American Archivists.

## What's Going On?

This plugin modifies two functions in ArchivesSpace's EAD serialization script to include a new attribute.

Collection-level `<unitid>` are generated in the `stream()` function, at line 66, and in the `serialize_child()` function, at line 150.

This plugin uses [Nokogiri Builder](http://nokogiri.rubyforge.org/nokogiri/Nokogiri/XML/Builder.html) to add attributes to XML tags, using the syntax of `xml.TAGNAME(ELEMENT_VALUE, :ATTRIBUTE_NAME => ATTRIBUTE_VALUE)`

## Installing the Plugin

* Download this repository into `{YOUR_ARCHIVESSPACE_DIRECTORY}/plugins/saa-aspace-demo`
  * The plugin file should be at `{YOUR_ARCHIVESSPACE_DIRECTORY}/plugins/saa-aspace-demo/backend/model/saa-ead.rb`
* Add `'saa-aspace-demo'` to the `AppConfig[:plugins]` line of `{YOUR_ARCHIVESSPACE_DIRECTORY}/config/config.rb`
  * e.g. `AppConfig[:plugins] = ['saa-aspace-demo', 'local', 'lcnaf', 'aspace-public-formats']`
* Start (or restart) your ArchivesSpace instance
  * If all went well, on EAD export, you should see `<unitid type="local_mss">` replace `<unitid>`