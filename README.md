# Metroid

## Index

[Overview](#overview)

[Installation](#installation)

[Usage](#usage)

[Citing METROID](#citing-metroid)

[Funding](#funding)

[License](#license)

## Overview

METROID (Morphological Extraction of Transmembrane potential from Regions Of Interest Device) is a computational tool to filter cellular  transmembrane potential signals obtained from low signal-to-noise ratio (SNR) regions of interest (ROIs) in single cell fluorescence images. Metroid can be executed as a software with a graphical user interface (Windows only, click [here](https://figshare.com/s/4bdcdc7826620464adec) to download the installer) or its code can be run in jupyter notebooks (check the [Examples](/Examples) folder). A simplified flowchart is shown below:

![Metroid_flowchart](/Metroid_flowchart.png)

The user should provide a membrane potential fluorescence video of a single cell, the video frame rate and an input variable that indicates if the expected signal is supposed to be transitory (like an action potential, AP), perdurable like an irreversible electroporation signal) or if there is no signal (only used to check system noise levels). A brightfield snapshot is also required if running the code in jupyter notebook.

Then, Metroid can either load or generate a cell mask (a binary image file delimiting where the cell is), divide it into ROIs of similar area in a standardized fashion, and get these ROIs means over time. After that, it can fix photobleaching (optional).Finally it uses one out of 4 Blind Source Separation (BSS) methods, some of which include wavelets filtering, to separate signal from noise and rebuilds the signals without the noise components. The notebook version also provides a calibration sequence in order to convert the fluorescence signals into transmembrane potentials.

## Installation

To use Metroid as a software, you just need to download the installer [here](https://doi.org/10.6084/m9.figshare.11344046.v1), follow the straightforward installation procedure and run the application.

To use Metroid by running its code, you need to have python installed (we recommend installing [Anaconda](https://www.anaconda.com/distribution/), one of the most popular Python platforms). Then, [create a virtual environment](#creating-a-virtual-environment), [clone this repository into your machine](#cloningdownloading-metroid-repository), open jupyter notebook and run the code, eventually changing the default parameters to your data.

#### Creating a virtual environment

We recommend creating a new virtual environment because Metroid runs with certain specific package versions. You can do this with Anaconda.

##### Option1: Creating a virtual environment with Anaconda Navigator (Windows)

Open Anaconda Navigator, click on "Environments" tab and then click on the "Create" button. Give your new environment a name, make sure that the "Python" option is checked and, from the dropdown list select "3.6", then click "Create".

Your new local environment was created ! You need to add a few more packages. First go back to the Home tab and Install jupyter Notebook. Then, go back to Environments tab, click on the triangle right in front your environment's name and select "Open Terminal". Then type:

`pip install numpy matplotlib scikit-image==0.15.0 scipy scikit-learn statsmodels ipywidgets`    
and    
`jupyter nbextension enable --py widgetsnbextension --sys-prefix`

Done! Your environment is now set up! You environment will be active as long as it is selected in the "Environments" tab.

##### Option2: Creating a virtual environment with Anaconda prompt (Windows) or a Terminal (Linux)

Open Anaconda Prompt or a Terminal (in Linux) and type (you may replace "metroid_env" by another name for your local environment):

`conda create -n metroid_env python=3.6 numpy matplotlib scikit-image==0.15.0 scipy scikit-learn statsmodels ipywidgets` 

When conda asks you to proceed, type `y` or `yes`.
`conda command not found`? You should [add anaconda to your path](https://askubuntu.com/questions/908827/variable-path-issue-conda-command-not-found). 

Done! Your environment is now set up! Now let's activate it by typing the following:

`conda activate metroid_env`

(remember, if you chose a different name, you should replace `metroid_env` by your environment's name)
You should see your environment's name now in front of each new line. Then type:    
`jupyter nbextension enable --py widgetsnbextension --sys-prefix`

#### Cloning/Downloading Metroid Repository

You can clone this repository to your local machine by clicking on the "Clone or download" button and either download Metroid as a zip file or copy the metroid address to clone the repository. To clone the repository into a specific location, you can open Anaconda prompt (or a Terminal in Linux), navigate to your destination folder and type `git clone https://github.com/zoccoler/metroid.git`. If the cloning process is successful, a new sub-directory (metroid) appears on your local drive in your current directory.

## Usage

### Metroid Software (Windows)

Run Setup_METROID.exe and follow the installation procedure. After that, open METROID executable file and the main interface should appear (it may take a couple of minutes the first time). We suggest running the Examples first ('File->Load Default Data' and choose a video) to explore the software options.

Overall, load your data, click on 'MESS' button to generate ROIs and then click on 'Run' button to filter ROI signals using the parameters shown in the Parameters Box. Done! 
To see the results, double-click over each ROI! You can also 'Save ROIs' to save the generated ROIs as an image file (label_ROIs.tif) with each pixel having the corresponding ROI label number, and 'Save Outputs' to save the filtered signals both as images and as a .csv file, which can be imported by other softwares such as Microsoft Excel or MATLAB.

### Metroid notebooks

Go to Home tab, Launch jupyter Notebook, navigate to Metroid folder and run a notebook (for example, open [Example_Cell1.ipynb](/Examples/Example_Cell1.ipynb) and either run it cell by cell or click 'Cell->Run All'). Also, each part of Metroid also contains an example that you can run inside the respective notebook (for example, you can automatically or manually draw a cell mask by running [MESS.ipynb](/MESS.ipynb)).

## Citing METROID

Zoccoler, M., de Oliveira, P.X. METROID: an automated method for robust quantification of subcellular fluorescence events at low SNR. BMC Bioinformatics 21, 332 (2020). https://doi.org/10.1186/s12859-020-03661-9

## Funding

This project was funded by [São Paulo Research Foundation (FAPESP)](http://www.fapesp.br/en/) grant Proc. N 2011/51199–6 and [Coordination of Improvement of Higher Education Personnel (CAPES)](https://www.capes.gov.br/).

## License

METROID: Morphological Extraction of Transmembrane potential from Regions of Interest Device
Copyright (C) 2020  Marcelo Zoccoler and Pedro Xavier de Oliveira

This program is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License for more details (https://www.gnu.org/licenses/).
    
If you use this software in your research, please give appropriate credit by kindly citing us.
