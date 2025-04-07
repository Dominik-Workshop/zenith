## Main requirements for the distance sensors:
- high refresh rate (above `50 Hz`, preferably closer to `100 Hz`),
- measurement distance range from close to `0 m` to at least `1 m`.
## Candidates:
| MPN      | refresh rate [Hz] |  range [m]  | Multi zone | FoV (diagonal) [°] | I²C speed [kHz] | Notes                                          |
| -------- | :---------------: | :---------: | :--------: | :----------------: | :-------------: | ---------------------------------------------- |
| VL53L0X  |       ~50?        |      2      |     No     |        ~25         |                 |                                                |
| VL53L4CX |        30?        |  0.01 - 6   |     No     |         18         |      1000       |                                                |
| VL53L4CD |        100        | 0.001 - 1.2 |     No     |         18         |      1000       |                                                |
| VL53L5CX |        60         |      4      |    8x8     |         63         |      1000       |                                                |
| VL53L7CX |        60         | 0.01 - 3.5  |    8x8     |         90         |      1000       | Pin-to-pin and driver compatible with VL53L5CX |

1. **VL53L0X Refresh Rate:** Depends on the timing budget set. 50Hz requires a short budget (e.g., 20ms), which can reduce maximum range and accuracy, especially in difficult conditions. 33Hz (30ms budget) is more common for better reliability.
2. **VL53L0X Range:** The 2m is under ideal conditions (good target reflectance, low ambient light). Practical range against non-ideal targets is often closer to 1-1.2m. Minimum distance is around 30mm.
3. **VL53L5CX/L7CX Refresh Rate:** 60Hz is typically quoted for the full 8x8 resolution mode. Faster rates might be achievable with lower resolution (e.g., 4x4).

**Analysis based on your requirements ( >50Hz, 0-1m+):**

- **VL53L0X:** Borderline refresh rate, practical range might be just sufficient. Older technology.
- **VL53L4CX:** Meets refresh rate, excellent range (more than needed). Narrow FoV requires precise aiming or multiple sensors.
- **VL53L4CD:** Meets refresh rate, range is perfectly suited (0-1.3m). Narrow FoV. Seems like a very good candidate if single-point detection is sufficient.
- **VL53L5CX:** Meets refresh rate (60Hz). Range is good. Multi-zone (8x8) and wide FoV (63°) are major advantages for minisumo, allowing detection over a wider area and potentially understanding opponent angle/position better. Strong candidate.
- **VL53L7CX:** Similar to L5CX but with an even wider 90° FoV. Excellent for covering a large area in front of the robot with potentially just one sensor, though resolution per degree is lower. Strong candidate.
  
  
  # Curent favourites:
- **VL53L7CX** - 60Hz but multizone, 3 of them can cover 180deg
- **VL53L4CD** - 100Hz fastest one