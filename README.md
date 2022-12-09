This is a fork of [https://github.com/WachowiakLab/OdorMappingData](WachowiakLab/OdorMappingData) to facilitate working with the data from [1] in python. 

# OdorMappingData
Glomerular response datasets. 

Credits: S. Burton (data collection, analysis), A. Brown (analysis), M. Wachowiak (analysis), T. Rust (software).

Parent manuscript: [1]

See Materials and Methods of above paper for details of data collection and pre-processing pipeline. Description of .mat file is below:

‘odormappingdata_simple_05_22.mat’ file. <br/>
Variables:<br/>
	'allrespmatrices_dF': Structure array consists of odorant response matrices and ROI positions for each OB. Variables are indexed in the following order: (1) omp111L, (2) omp111R, (3) omp112L, (4) omp112R, (5) omp113L, (6) omp113R, (7) omp114L, (8) omp114R. All odorants are in the same order for all response matrices (see ‘odornameslist’ variable).<br/>
ROI positions indicate centroid of each ROI, after visual registration by aligning the midline and caudal sinus. Units are microns, reference (zero) is midline (for ‘Xpos’) and caudal sinus (for ‘Ypos’). Note that the Xposition for ROIs from the left OB is negative relative to midline.<br/>
	'allconcs_prep': Calculated final delivered concentration of each odorant, indexed in the same order as response matrices and odornames list, for each mouse, in mols/L. Note that concentrations estimated from vapor pressure, calibrated air dilution, and liquid dilution, assuming ideal behavior. <br/>
	'odornameslist': List of all 185 odorants (plus two vehicle controls), indexed in same order as odors in response spectrum matrices.<br/>

# Python-specific changes
1. Data is made available as pickled files, as a convenience for Python users.
2. Creation process is documented in a jupyter notebook.
3. Making available the `ROIPos` data that was not accessible from Python previously.

# Files
* `elife22data_python.pkl`: The data. Contains a dictionary with keys:
  * `'allresp'`: all repsonse matrices concatenated together. Rows: ROIs/glomeruli, columns: odorants. 
    `'allrespnorm'`: like `allresp`, but normalised. See original data description and paper for details. 
    `'roipos'`: Positions X,Y of ROIs. X is the lateral axis, X=0 is the bulb midline. Y is the frontal/caudal axis.  
    `'ranges'`: the row ranges in which the individual measurement blocks are contained. See `mousenames`.
    `'mousenames'`: The names of the indivisual measurements, i.e. mice and bulb sides. 


# References
[1] Mapping odorant sensitivities reveals a sparse but structured representation of olfactory chemical space by sensory input to the mouse olfactory bulb.
Shawn D. Burton, Audrey Brown, Thomas P. Eiting, Isaac A. Youngstrom, Thomas C. Rust, Michael Schmuker, Matt Wachowiak<br/> 
https://elifesciences.org/articles/80470
