# EPANET Water Distribution Network: Hazrat Shahjalal International Airport

Hydraulic modelling of a water distribution network for Hazrat Shahjalal International Airport (Dhaka) in EPANET, with 24-hour extended-period results for node pressures and pipe flows.

## Overview

The network was built and simulated in EPANET, and the results were extracted for selected nodes and pipes across the day.

## Results Included

| Item | Output |
|---|---|
| Network layout | Water distribution network schematic for the airport |
| Pressure at nodes 125 and 17 | Time-series plots |
| Discharge and velocity in pipes 108 and 76 | Time-series plots |
| Pressure at node 200 | First 12 hours (00:00–12:00) |
| Velocity and discharge in pipe 76 | Last 6 hours (19:00–24:00) |

All plots are in [`report/EPANET_Results.pdf`](report/EPANET_Results.pdf).

## Repository Structure

```
├── report/    # EPANET_Results.pdf (network map and result plots)
└── README.md
```

Suggested addition: the EPANET input file (`.inp`) so others can open and rerun the model.

## Tools

EPANET 2.x

## Author

Kaif Al Shahriar Qais Shurid
