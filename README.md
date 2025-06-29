## A precision current source that can be configured for currents up to ~10mA.

I needed to verify the current measurement accuracy of the low-current ranges of my data logger and a reference for calibration purposes. Since I don’t own a programmable current source like a Keithley 220 or SMU, I came up with this approach instead. Check [here](https://tobiasnetzer.github.io/posts/current-source/) for more info.

Documentation
- [Schematic](https://github.com/TobiasNetzer/PrecisionCurrentSource/blob/main/Documentation/Schematic.pdf)
- [Assembly Drawing](https://github.com/TobiasNetzer/PrecisionCurrentSource/blob/main/Documentation/Assembly%20Drawing.pdf)
- [BOM](https://htmlpreview.github.io/?https://github.com/TobiasNetzer/PrecisionCurrentSource/blob/main/Documentation/BOM.html)

---

<img src="https://github.com/TobiasNetzer/PrecisionCurrentSource/raw/main/Documentation/Render%20Both.png">

## Limitations of the Design

Because CR2032 coin cells have a high internal resistance, they can’t deliver very high currents. This limits how much current the current source can provide. The op-amp also plays a limiting role here, since it can’t handle sinking large currents. As a result, this current source is only suitable for currents up to around 10 mA. Additionally, since the voltage swing across the load is limited to 1.4V, the maximum load at, for example, 1mA cannot be higher than 1.4kΩ. This limits the usable range of the current source further.

## First Tests

The design has not been fully tested yet! The output current has been measured to be within ±0.2%.

| Configured Current &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;          | Measured Current &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;        | Error &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;           |
| ---                                                                   | ---                                                               | ---                                                       |
| 100nA                                                                 | 99.82nA                                                           | -0.18%                                                    |
| 1µA                                                                   | 0.999µA                                                           | -0.1%                                                     |
| 100µA                                                                 | 100.07µA                                                          | 0.07%                                                     |
| 1mA                                                                   | 0.999mA                                                           | -0.1%                                                     |

Several other aspects such as load regulation, temperature stability and ripple/noise should also be tested. However, I currently lack the equipment to accurately perform these tests.

I did sample the output current with my datalogger at 1kHz to get an idea of how noisy the current source is. These results should be taken with a grain of salt, since the logger’s ADC does some internal averaging and I don't have a known reference to test the logger against.

| Current Source &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;          | Peak-Peak Current &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;     |
| ---                                                               | ---                                                             |
| 1µA                                                               | 1.23nA                                                          |
| 100µA                                                             | 73.25nA                                                         |
| 1mA                                                               | 1.24µA                                                          |

<img src="https://github.com/TobiasNetzer/PrecisionCurrentSource/raw/main/Documentation/images/test_result.png">