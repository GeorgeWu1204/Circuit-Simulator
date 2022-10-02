# Circuit-Simulator
ELEC40006 Electronics Design Project 

This repository contains the circuit simulator project, which is the 1st Year end-of-year project for Imperial College London EIE department. This project scores 71.23% overall. The program attempt to realize the same functionality as the SPICE. It could conduct AC and DC analysis for various circuits including diodes with ideal accuracy. 

# How to run this code

:star: find_final_sol: This makes sure that the user only needs to input the name of this function and instructions in the main, and the rest of the instructions would appear in the terminal. The order of the implementation of the function is as follows: 

1) Input stage
The program asks the user to give the name of an input file and then uses ReadInput to take in the content in the given file. With the given file, setting generates components accordingly, and ac and frequency obtain the list of frequencies required for the analysis. Before moving on to the next stage, we built upon what is required by the specification by allowing the user to choose the desired input source when there is more than one source. To make a choice clear, we created two vectors storing voltage and current sources, respectively, with a serial number and its designator. A third vector is created to store the designators of both sources, which is used as an indicator of the total number of input sources. When more than one source is detected, the program enters the if condition and prints the list of sources available for the user to choose. The user needs to enter the serial number corresponding to the desired input source, and then the value (voltage or current) will be found and assigned to a variable representing the input of type complex double (used later in the function). Another choice that needs to be made by the user is to nominate an output node. The program provides number ranging from 1 to the maximum number of nodes in the circuit for the user to choose from.

2) DC operating point
get_standart_volt obtains useful node voltages in preparation for small-signal parameters of certain components.

3) Small-signal analysis
This makes use of functions reorganizedc, classify_comp, shortdcsource to prepare the data needed. Then the program does the analysis with each required frequency. The output is a matrix of type complex double, and the program locates the voltage corresponding to the user’s choice of the output node. At last, transform this into magnitude and phase, and store in the vectors, respectively.

4) Output stage
The program asks the user to enter the name of the pre-created file that would store the output. The output has three values: frequency, magnitude, and phase (in degrees) of the transfer function calculated at that particular frequency, spaced using tab and written line by line according to the content of the three vectors.
