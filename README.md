# Cell-interacitng Condensate Rheology using Scanning Probe Microscopy

This package contains tools for evaluating microrheological experimental data, as presented in the associated paper (below).

Users are requested to cite:

Aida Naghilou, Tom M.J. Evers, Oskar Armbruster, Vahid Satarifard, Alireza Mashaghi,
Synthesis and characterization of phase-separated extracellular condensates in interactions with cells,
Chemical Engineering Journal, 164551 (2025)  Doi: 10.1016/j.cej.2025.164551.


1.	Accepted data formats: The Mathematica notebook accepts measurement files as generated by the instrument software. They have to contain the time coordinate, the measured head height, the smoothed measured head height, and the force. The file has to contain both the approach as well as the oscillation segments.
2.	Instructions: Specify the following
	* Measurement file name (variable `filename`) relative to the notebook location
	* Cell rheological properties file name (variable `filenameOfCellG`) relative to the notebook location
	* Particle radius (variable `particleRadius`)
	* Enable/disable surface energy compensation (variable `compensateSurfaceEnergy`)
	* Phase correction information (variables `phaseOffset` and `phaseSlope`)
	* Touchdown mode (variable `touchdown`):
		* Touchdown “Snap”: Specify the filter length (variable snapFilterLength), the keepout (variable snapKeepout) and the baseline length (variable snapBaselineLength).
		* Touchdown “Hard”: Specify the data length (variable hardLength).
		* Touchdown “Manual”: Specify the two intersection regions (variables ma1 to ma4).
	* Contact model (variable `contactModel`):
		* Contact model "Hertz": 
		* Contact model "StackedHertz":
3.	The notebook will produce a file named `G.dat` containing the complex shear modulus as a function of frequency.
4.	The provided `example_force_file.txt` can be used to determine the complex frequency dependent rheological behavior from the measured data by employing the provided code.

## Usage
At first, the rheological properties of the cells have to be determined. For this, measurement files from cells have to be evaluated with the following settings:
* `compensateSurfaceEnergy = False`
* `contactModel = "Hertz"`
* `particleRadius = ∞`
Use a scientific data analysis tool (e.g. Origin) to average the complex share moduli as a function of frequency (generated file `G.dat`) and provide the name of the file this data got stored to in the variable `filenameOfCellG`. Then, measurements of condensates resting on cells can be evaluated with `contactModel = "StackedHertz"`.
