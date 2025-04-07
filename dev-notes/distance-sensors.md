## Key Requirements: 
- **Refresh Rate:** > `50 Hz` (ideally closer to `100 Hz`) 
- **Range:** Close to `0 m` up to at least `1 m`
## Sensor Candidates Comparison:
| MPN      | refresh rate [Hz] |  range [m]  | Multi zone | FoV (diagonal) [°] | I²C speed [kHz] | Notes                                                                 |
| -------- | :---------------: | :---------: | :--------: | :----------------: | :-------------: | --------------------------------------------------------------------- |
| VL53L0X  |       ~50?        |      2      |     No     |        ~25         |       400       | Older gen; Rate & practical range depend heavily on budget/conditions |
| VL53L4CX |        30?        |  0.01 - 6   |     No     |         18         |      1000       |                                                                       |
| VL53L4CD |        100        | 0.001 - 1.2 |     No     |         18         |      1000       | Fast; Optimized for required range (0-1m); Narrow FoV                 |
| VL53L5CX |        60         |      4      | Yes (8x8)  |         63         |      1000       | Good FoV & range balance                                              |
| VL53L7CX |        60         | 0.01 - 3.5  | Yes (8x8)  |       **90**       |      1000       | **Widest FoV**; Pin/driver compatible w/ L5CX                         |
| VL53L8CX |        60         |  0.01 - 4   | Yes (8x8)  |         65         |      1000       | Square FoV (45°x45°); Newer gen                                       |

## Top Candidates & Strategy Considerations:

1.  **VL53L7CX (Focus on Coverage & Tracking):**
    * **Pros:** Widest FoV (90°) combined with 8x8 zones allows for excellent opponent detection and tracking over a large area with potentially fewer sensors (e.g., three for 180°). 60Hz rate is sufficient.
    * **Cons:** Lower angular resolution per zone compared to narrower FoV sensors.

2.  **VL53L4CD (Focus on Speed & Simplicity):**
    * **Pros:** Highest refresh rate (100Hz). Range is perfectly suited. Simpler single-point data.
    * **Cons:** Narrow FoV (18°) requires multiple sensors (4-6+) for good frontal coverage, increasing cost/complexity and providing less positional information than multi-zone.

**Decision Factors:**
* Prioritize **maximum speed**: Choose **VL53L4CD**.
* Prioritize **wide-area detection and opponent location tracking** with fewer sensors: Choose **VL53L7CX**.
* Consider **VL53L5CX/VL53L8CX** as balanced multi-zone alternatives if their specific FoV is preferred or they are more readily available/cost-effective.