## CTD Data Standardized Data Processsing

Hakai follow the standard data processing procedures suggested by either the scientific community of the instrument manufacturer.

<p align="center">
<img src="figures/Hakai-ctd-processing-workflow-figure-3-processing.png" alt="Processing" width="600"/>
</p>

### RBR Data Processing

The Hakai RBR CTD Profiles standard processing procedure follows the recommandations provided within the Report [Guidelines for processing RBR CTD profiles](https://waves-vagues.dfo-mpo.gc.ca/library-bibliotheque/40578112.pdf) and RBR recommendations.

The main matlab tool used to process Hakai RBR CTD profiles is maintained and available at [hakai-data-tools/ctd-tools/rbr-proc](https://github.com/HakaiInstitute/hakai-data-tools/tree/master/ctd-tools/rbr-proc).

Where essentially the MatLab script [process_unprocessed_hakai_profiles.m](https://github.com/HakaiInstitute/hakai-data-tools/blob/master/ctd-tools/rbr-proc/process_unprocessed_hakai_profiles.m) is run every 5 minutes on the Hakai server Hecate to retrieve and process the unprocessed profiles available within the Hakai database ctd.ctd_file_cast view through the api endpoint `/ctd/views/file/cast`:

Only the profiles respecting the [following api filter conditions](https://github.com/HakaiInstitute/hakai-data-tools/blob/ef34172f6e3e8c858f2379ad473cb10422ca6f85/ctd-tools/rbr-proc/process_unprocessed_hakai_profiles.m#L49) are processed:

```matlab
filterURL = [
        'processing_stage=1_datCnv',...
        '&(status!=MISCAST|status=null)',....
        '&process_error=null',...
        '&device_model={XRX-620,RBRconcerto3,XR-620,RBRconcerto,RBRmaestro,RBRmaestro3}',...
        '&limit=-1'...
        ];
```

Resulting processed data is then uploaded back to the Hakai Database ctd.ctd_cast_data table and the processing_stage associated to each specific processed casts is updated to `processing_stage = '8_rbr_processed'`.

Any errors or warnings encountered are uploaded to:

- ctd.ctd_cast `processing_errors` column
- Sentry related project [rbr-proc](https://sentry.io/organizations/hakai-institute/projects/rbr-proc/?project=282260).

#### Static Deployment

A static deployment is a special case where the instrument has to be maintained at a specific location and depth for a minimum duration.

This type of deployment has been implemented to provide the ability to sample regions associated with very shallow waters.

To be considered as a static measurement, a sample needs to respect the following conditions:

```
1. The instrument needs to be **maintained at a specific location and depth for at least 2 minutes and 30 seconds** (We recommend leaving the instrument for at least 3 minutes).
2. The depth throughout that period can only vary by either 10cm, 33% of the depth or up to 1m, whichever is greater.
3. The instrument needs to be deeper than 10cm in the water.
```

#### Dynamic Deployment

The dynamic deployment corresponds to a profile measurement. For a more detailed description of the procedure as recommended by the Hakai Institute, please refer to the [Hakai CTD Profile Data Processing Manual](https://docs.google.com/document/d/1ARnOcHvuxj4usH8uhaMJyEGsSERe2cTW4V0jl5DUO00/edit?usp=sharing).

### Seabird Data Processing

Hakai Seabird Data Processing workflow follow closely the recommendations provided by Sea-Bird within the [SBE Data Processing Manual](https://www.seabird.com/asset-get.download.jsa?code=251446). Hakai essentially uses a python wrapper to interface the Seabird SBEDataProcessing software to run the different processing steps involved in the standard processing of the Seabird CTD data.

The Python wrapper to interface the Seabird SBEDataProcessing software maintained and available within the [hakai-data-tools/ctd-tools/seabird-proc/](https://github.com/HakaiInstitute/hakai-data-tools/tree/master/ctd-tools/seabird-proc) repository.

The python wrapper match for a given SBE hex file, the related instrument serial number and the closest xmlcon calibration file available within the [xmlcon files directory](https://github.com/HakaiInstitute/hakai-data-tools/tree/master/ctd-tools/seabird-proc/xmlcon) prior to the collection date.

Once the data converted from their raw hexadecimal data to the engineering format a series of processing steps are applied to the data by following the nearest in time prior processing parameter PSA files associated with this instrument serial number within the [PSA folder](https://github.com/HakaiInstitute/hakai-data-tools/tree/master/ctd-tools/seabird-proc/psa).

Since the SBEDataProcessing Software is only available for windows. The tool is runned within a dedicated server hosted within the Hakai Victoria Wharf street office.
