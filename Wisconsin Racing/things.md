Steering wheel (done, but always improving)
- Converted from sd card to cm4 eeprom
- Fixed dials
    - Added screen
    - How drivers change launch control and traction control (for the future)
- Fixed e-car blank screen
- Organized code significantly
- Added and removed GUI depending on what was wanted
- Used ssh and vnc to modify raspberry pi
- Used CAN
- Multithreading 
- Took driver input, made it real
- Fixed CAN freezing

---

Labjack logging (done)
- https://github.com/theradest1/Labjack-scripts 
- Labjack T7 Pro
- Uses Lua
- Also learned how to use it with python
    - Ended up having no improvements and had to be linked to computer (raspi)
- 5 strain gauges
- Voltage difference

---

Engine Tooning With Dyno:  (10/0/24 - 12/25/24)
- https://gitlab.com/wisconsinracing/ECUFiles/-/tree/main/Logging/DynoPythonTools 
- Take in logged data (mdf)
- Process it
- Used pandas library
- Get many graphs and data for tuning:
    - Cyl1 vs Cyl2 Phi difference
        - Generates a map of cyl1 phi/cyl2 phi 
        - Multiply with current cylinder phi map
        - Makes them equal
        - Allows for balanced cylinder loads (thus more power)
    - Cyl phi (average) vs target phi difference
        - Similar to previous, but for making the ecu more accurate at setting phi
        - More confident about setting values
    - Map of sample count:
        - To make sure that enough samples of each cell was ran
    - Spark advance vs torque reduction:
        - For generating a simple version of a torque model
        - Can be used for traction/launch control to get an exact torque very quickly
        - Plots the torque reduction from the max torque of linked RPM 
    - BSFC:
        - ![Graph](Wisconsin%20Racing/Pictures/BSFCpng.png)
        - Brake-specific fuel consumption
        - the fuel (grams) per kW*hr for each rpm and torque
        - Used for finding (and improving) the efficiency of the engine
    - And more less important ones
- Store past parsed/computed data
    - Allows for really quick additional data
- Generate several types of visual representations of the data
    - Heatmaps
    - Smoothed heatmap
        - contour lines
    - 3d graph
    - Smoothed and subdivided 3d graph
    - Makes it easier to see data
    - Very pretty (:
- Interpolation of data
    - While collecting data, many times you will have holes from not having enough samples, and this is especially common when doing engine load sweeps.To keep from including outliers in the data, we often have sample thresholds that only use data that has enough samples. 
    - Instead of doing it by hand, I made a program for it
    - It never overwrites data, it only fills in places where there weren't enough samples.
    - I also made it prioritize missing data that has more filled in surrounding cells to keep from having weird patterns in the graphs
---
Torque Model (ECUFiles/Logging/TorqueModel):
Took data from dyno
Spark retard, RPM, Load (pedal %), 

Traction control (not done)
Feedforward for launch control
Tunable model that is time vs torque
Stability control
Yaw based



New ECU CAN:

