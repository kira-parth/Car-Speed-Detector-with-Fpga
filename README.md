# Car-Speed-Detector-with-Fpga
it includes speed detection with nexys4ddr with help of two ir sensor
Design Details:
  1.	Inputs:
       *clk: System clock for all operations.
       *ir_sensor1, ir_sensor2: Signals triggered by cars passing through sensors.
2.	Outputs:
      *	abcdefg: Seven-segment display segments.
      *	an: Enable signals for multiplexing seven-segment displays.
      *	rgb: RGB LED outputs (3 bits for Red, Green, and Blue).
3.	Parameters:
      *	DISTANCE_CM = 10: Fixed distance between the two IR sensors.
4.	Registers:
     o	timer: Global clock cycle counter.
     o	time1, time2: Time captures for ir_sensor1 and ir_sensor2 events.
     o	time_diff: Time difference between sensor triggers.
     o	speed_reg: Stores the calculated speed.
     o	digit: Holds the current digit being displayed on the seven-segment display.
     o	active_digit: Determines the active display in multiplexing.
     o	refresh_counter: Counter to control multiplexing refresh rate.
5.	Key Functional Blocks:
     o	State Machine:
      	Manages sensor-triggered events.
      	Records timestamps for each sensor's activation and resets state.
o	Speed Calculation:
	Computes speed using the formula: Speed=Distance (cm)×100Time Difference (clock cycles)\text{Speed} = \frac{\text{Distance (cm)} \times 100}{\text{Time Difference (clock cycles)}}Speed=Time Difference (clock cycles)Distance (cm)×100
o	RGB LED Control:
	Categorizes and outputs speed levels using RGB LEDs.
o	Seven-Segment Decoder:
	Converts digits to their respective segment patterns.
o	Multiplexing Logic:
	Cycles through six displays for speed visualization.
