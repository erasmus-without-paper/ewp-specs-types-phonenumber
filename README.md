EWP Phone Number Types
======================

* [What is the status of this document?][statuses]
* [See the index of all other EWP Specifications][develhub]


Summary
-------

This repository contains XML Schemas used in EWP APIs for encoding phone and
fax numbers. It follows the same [versioning rules][compat-rules] as all EWP
APIs do. Other projects are welcome to reuse this schema, along with its
namespace. We are also open to suggestions of extending it.


About this data type
--------------------

### About E.164 standard

As opposed to [addresses][specs-address], phone number formats were much
easier to decide upon, because there already exists an international standard
for handling those.

You can read more on this standard:

* [on our issue pages][discussion],
* [on Twilio's support pages][twilio-article],
* [on Wikipedia](https://en.wikipedia.org/wiki/E.164).


### Compatibility and conversions

There are free libraries, such as Google's [libphonenumber]
(https://github.com/googlei18n/libphonenumber), which allow you to convert
between national phone numbers and E.164. This means that clients will be able
to "pretty print" such number, and server should also be able to easily provide
them in E.164 format.

However, if - for some reason - the server is not able to convert its data to
E.164 format, we allow it to be provided in unformatted way too (with the
`<other-format>` element).


The Schema
----------

See attached [`schema.xsd`](schema.xsd) file.


Examples
--------

```xml
<phone>
    <e164>+4723456789</e164>
</phone>
```

```xml
<phone>
    <e164>+4722222222</e164>
    <ext>3407</ext>
</phone>
```

```xml
<fax>
    <!-- To be avoided. -->
    <other-format>(23) 456789</other-format>
</fax>
```


[develhub]: http://developers.erasmuswithoutpaper.eu/
[statuses]: https://github.com/erasmus-without-paper/ewp-specs-management#statuses
[compat-rules]: https://github.com/erasmus-without-paper/ewp-specs-architecture/#backward-compatibility-rules
[discussion]: https://github.com/erasmus-without-paper/ewp-specs-architecture/issues/15
[specs-address]: https://github.com/erasmus-without-paper/ewp-specs-types-address
[twilio-article]: https://support.twilio.com/hc/en-us/articles/223183008-Formatting-International-Phone-Numbers
