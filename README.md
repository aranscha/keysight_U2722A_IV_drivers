# Keysight U2722A IV-Curve Measurements
This repository contains several drivers for measuring transistor IV-curves of single or two-transistor configurations for the Keysight U2722A SMU (https://www.keysight.com/us/en/products/source-measure-units-smu/u2722a-u2723a-usb-modular-source-measure-units-smu.html). A detailed description of every VI-file, along with a use case is given below. `SMU_IV single.vi` uses a single U2722A SMU, but the other Virtual Instruments (VIs) require 4 SM channels, so 2 SMU's are needed. Using LabView drivers instead of the proprietary PathWave BenchVue Software has the advantage of having a more detailed control over the experiments.

## `SMU_IV single.vi`
Simple current-voltage characterization of a transistor (https://en.wikipedia.org/wiki/Current%E2%80%93voltage_characteristic). For each gate voltage, the drain-source voltage is swept over a certain range. The interface of this program is shown below:

![](README_figs/IV%20single%20interface.PNG)
## `SMU_IV dual.vi`
Analogous to the previous experiment, but using an additional SMU to concurrently and independently characterize 2 transistors. This is useful when characterizing a large amount of transistors, e.g. on a wafer.

## `SMU_IV_gate_2_sweep.vi`
The purpose of this program is illustrated in the figure below:

![](README_figs/SMU_gate_2_constant%20illustration.PNG)

This setup allows for a variety of configurations. In the simplest case, you can have a transistor with a resistive load. In this example, T2 represents an active load in a p-mode cascode, where the gate voltage can be swept or kept constant.

The interface of the instrument is shown below:
![](README_figs/IV%20arbitrary%20interface%201.PNG)
![](README_figs/IV%20arbitrary%20interface%202.PNG)

## `SMU_IV_gate_2_constant.vi`
Similar to the previous VI, but simpler in the sense that only the first gate voltage is swept, while the second gate is biassed by a constant voltage. Thus, the previous program is more general.

## Note about logging the data
New data is appended to the target file, to ensure that experiments are not accidentally overwritten. For the two-transistor configurations, the order of the sweeps is as follows: gate 1 (the "input"), Vdd, gate 2 (if not constant). This should help with the interpretation of the results.

## About
These drivers were written for the Translational Neuroelectronics Lab at Columbia University, led by Prof. Dion Khodagholy (https://www.dion.ee.columbia.edu/).