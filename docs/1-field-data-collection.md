## Field Data Collection

Data is first collected in the field by the field crew. The minimum required equipment is a CTD instrument unit and a tablet or phone (Android or iOS) with the [Device Magic](https://www.devicemagic.com/) application installed on it linked to the Hakai Device Magic account.

### Field Metadata from form (Device Magic app)

Every time the field crew is leaving on a survey, a new `CTD form` should be created within their tablet. To which is added all the survey-related information, all the drops completed during the survey including the miscasts ones should be added to the form as a drop.

Every drop must be associated with a start/bottom/end time, a station, and a start/bottom/end location (highly recommended).

### CTD Instrument (RBR Maestro/Concerto/XR620 or Seabird 19V2)

Hakai workflow is compatible with two CTD instrument manufacturer and their respective following profiling instruments:

#### [Sea-Bird Scientific](www.seabird.com)

The compatible instruments include:

1. [SBE 19plusV2](https://www.seabird.com/sbe-19plus-v2-seacat-profiler-ctd/product?id=60761421596)
2. [SBE 911 plus](https://www.seabird.com/sbe-911plus-ctd/product?id=60761421595) (potentially)
3. [SBE 25 plus](https://www.seabird.com/sbe-25plus-sealogger-ctd/product?id=60429374753)) (potentially)

Hakai as of now only supports the SBE 19V2 instrument, that being said, it would be possible to support with very little effort any other profiling instruments from the manufacturer. Please refer to the [Seabird 19plusV2 Standard Operation Protocol manual](https://docs.google.com/document/d/1KFa8QB3JSkSBwPwUhb_FH8x_sM3v4mOx-pAeTz3_xDk/edit?usp=sharing) for a more detailed walkthrough of the different steps associated with the use of the Seabird Instruments as recommended by the Hakai Institute.

#### [RBR](www.rbr-global.com)

The compatible instruments include:

1. XR-620
2. Concerto (recommended Fast)
3. Maestro (recommended Fast)
4. [Concerto3](https://rbr-global.com/products/standard-loggers/rbrduo-ct/) (recommended Fast)
5. [Maestro3](https://rbr-global.com/products/standard-loggers/rbrmaestro/) (recommended Fast)

Please refer to the [Hakai RBR Instruments Standard Operation Protocol Manual](https://docs.google.com/document/d/1CdPT_7pTRghaBxCO5jRZT-BRfMDt4W194HIRs06M6A4/edit?usp=sharing) for a more detailed walkthrough of the different steps associated with the use of the RBR Instruments as recommended by the Hakai Institute.

### Bottle Mounted Pressure Gauges

The Hakai Institute uses small boats during its regular surveys which prevents the use of a larger rosette system for collecting water. Instead, Hakai relies on Niskin bottles of different volumes mounted at different locations on a line to sample specific target depths.

The bottles are first lowered into the water column to reach the target depths. Once the bottles are at the right depth, a messenger is sent from the surface to trigger sequentially the different bottles which each at their turn releases another messenger which gets dropped below that bottle to trigger the next bottle below.

In order to confirm the depth of each bottle when they get triggered, a small pressure gauge sensor ([RBR Solo](https://rbr-global.com/products/compact-loggers/rbrsolo/)) is mounted on each bottle and records the pressure associated with each bottle every second. This pressure data can be used to derive the associated depth of each bottle.

RBR Solo data is downloaded by the same software used by the RBR CTD instruments [Ruskin](https://rbr-global.com/products/software/)

### Field Data Storage

### Field Instrument Maintenance Forms
