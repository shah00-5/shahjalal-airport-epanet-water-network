# Hydraulic Analysis of the Shahjalal International Airport Water Distribution Network

Extended-period hydraulic analysis of the Shahjalal International Airport (Dhaka, Bangladesh) water distribution network in EPANET. The model estimates time-varying nodal demands and checks pressure, velocity and head loss at peak and minimum demand.



## Key results

| Metric | Result |
| --- | --- |
| Total base demand | about 128 LPS (127.99 LPS over 41 demand nodes) |
| Peak demand (7:00 AM) | about 220 LPS (multiplier about 1.73) |
| Minimum demand (3:00 AM) | about 51 LPS |
| Lowest pressure at peak | 22.04 m at Junc 22a (source head assumed 25 m) |
| Highest velocity at peak | 1.17 m/s (Pipe 132), under the 2 m/s limit |
| Only head loss exceedance | Pipe 132, 150 mm, 11.79 m/km |
| Source split | Tank 1 supplies about 76% of demand at all hours |
| Zero-flow pipes | Pipes 119, 82a and 81 |

The network meets the pressure and velocity criteria at peak demand. It is oversized: most pipes run below 0.3 m/s, which raises water-age and sediment concerns, especially on the east branch.

## Network and data

- 93 junctions, all at elevation 0 m, from `Node demand data.pdf`
- 100 pipes, 10 to 825 m long, 100 to 450 mm in diameter, Hazen-Williams C of 100 to 140, from `Pipe network parameters.pdf`
- Two tubewell-fed source tanks (Tank 1 on the west side, Tank 2 on the east side)
- A 24-hour demand multiplier curve (morning peak at 7:00 to 8:00 AM, evening peak at 5:00 to 6:00 PM)

The layout is schematic and not drawn to scale.

## Method

1. Build the network in EPANET from the node and pipe data.
2. Apply the 24-hour multiplier pattern to the base demands (nodal demand = base demand x hourly multiplier).
3. Run a 24-hour extended-period simulation with a 1-hour time step, using the Hazen-Williams formula and flow units of LPS.
4. Read node pressures and pipe flow, velocity and unit head loss at 7:00 AM (peak) and 3:00 AM (minimum).
5. Compare results with the criteria: pressure of at least 10 to 15 m, velocity of 0.3 to 2.0 m/s, and unit head loss below 10 m/km.

## Assumptions and limitations

- No tank elevations or levels were given. Each tank is modelled as a constant-head reservoir with an assumed total head of 25 m, so all pressures depend on this value.
- The 24 hourly multipliers were read from a graph and are approximate.
- One demand pattern is applied to all demand nodes.
- Fire flow, leakage, pipe ageing and water quality were not modelled.
- The evaluation criteria are commonly used values, not a specific local standard.

## Recommendations

1. Upsize Pipe 132 from 150 mm to 200 mm and rerun the model.
2. Review the zero-flow spurs (Pipes 119, 82a and 81): loop them, add flushing points, or remove them.
3. Run a sensitivity check at source heads of 15, 20 and 25 m.
4. Run a water-age simulation for the east branch.
5. Check supply if Tank 1 is out of service.
6. Replace the assumed tank heads with site data.

## Repository contents

```
.
├── README.md
├── report/
│   └── Hydraulic_Analysis_of_the_Shahjalal_International_Airport_Water_Distribution_Network.docx
├── data/
│   ├── Node demand data.pdf
│   └── Pipe network parameters.pdf
├── model/
│   └── airport_network.inp      
└── figures/                     
```

## How to reproduce

1. Install [EPANET 2.2](https://www.epa.gov/water-research/epanet).
2. Open `model/airport_network.inp`.
3. Check that Hydraulics Options use the Hazen-Williams formula, flow units LPS, a 24-hour duration and a 1-hour hydraulic time step.
4. Run the simulation and use the time slider to view 3:00 AM and 7:00 AM.
5. Use Report, then Table, to export node pressures and link flow, velocity and unit head loss.

## Author

Kaif Al Shahriar Qais Shurid
