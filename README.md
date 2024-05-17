# gnatss-test-data

This repository is used to host test data for the GNATSS software.
The data is in a zip file hosted as a release asset in this repository.

See [Releases](https://github.com/seafloor-geodesy/gnatss-test-data/releases).

## Directory Structure

The zip file contains the following directory structure:

```console
2022
└── NCL1
    ├── 208
    │   ├── GPS_PPP
    │   │   └── GPS_POS_FREED
    │   ├── WG_20220727
    │   │   ├── RPH_TWTT
    │   │   ├── pxp_tt
    │   │   └── pxp_tt_j2k
    │   └── posfilter
    │       └── POS_FREED_TRANS_TWTT
    ├── 209
    │   ├── GPS_PPP
    │   │   └── GPS_POS_FREED
    │   ├── WG_20220728
    │   │   ├── RPH_TWTT
    │   │   ├── pxp_tt
    │   │   └── pxp_tt_j2k
    │   └── posfilter
    │       └── POS_FREED_TRANS_TWTT
    ├── 210
    │   ├── GPS_PPP
    │   │   └── GPS_POS_FREED
    │   ├── WG_20220729
    │   │   ├── RPH_TWTT
    │   │   ├── pxp_tt
    │   │   └── pxp_tt_j2k
    │   └── posfilter
    │       └── POS_FREED_TRANS_TWTT
    ├── NOV
    │   ├── NCL1_INSPVAA.dat
    │   └── NCL1_INSSTDEVA.dat
    ├── ctd
    │   └── CTD_NCL1_Ch_Mi
    ├── deletns.dat
    └── quality_control.csv
```

- `2022/NCL1`: The `2022` directory is the top level directory,
with `NCL1` being the station name and a subdirectory of the year.
- `208,209,210`: The `208`, `209`, and `210` directories are the day of the year.
  - `GPS_PPP`: The `GPS_PPP` directory contains the GNSS data.
  - `WG_*`: The `WG_*` directory contains the roll pitch heading (`RPH_TWTT`) and travel times data (`pxp_tt_*`).
  - `posfilter`: The `posfilter` directory contains the GNSS data after kalman filtering, spline interpolation, and rotation from the Fortran and Shell scripts.
- `NOV`: The `NOV` directory contains the `INS` data.
  - `NCL1_INSPVAA.dat`: The `NCL1_INSPVAA.dat` file contains the INS Position, Velocity and Attitude data. See Novatel [`INSPVA`](https://docs.novatel.com/OEM7/Content/SPAN_Logs/INSPVA.htm).
  - `NCL1_INSSTDEVA.dat`: The `NCL1_INSSTDEVA.dat` file contains the INS PVA standard deviations data. See Novatel [`INSSTDEV`](https://docs.novatel.com/OEM7/Content/SPAN_Logs/INSSTDEV.htm).
- `ctd`: The `ctd` directory contains the `CTD` data.
- `deletns.dat`: The `deletns.dat` file contains the deletions data from the Fortran software.
- `quality_control.csv`: The `quality_control.csv` file contains the quality control human generated data for GNATSS.

## Usage

The most direct way to use the data is using [`gnatss`](https://github.com/seafloor-geodesy/gnatss).
Within the `utilities` module there is a `testing` module that contains a function called `download_test_data`.
This function will download the test data from this repository and extract it to the specified `tests/data` directory or one that you specify.

```python
from gnatss.utilities.testing import download_test_data

# This will download the test data to the default directory
# of ${current working directory}/tests/data and unzip it.
download_test_data(unzip=True)
```

## License

This repository is licensed under the BSD 3-Clause License, see [LICENSE](LICENSE).
