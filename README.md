# PyNutil
PyNutil is currently under development.

PyNutil is a Python library for brain-wide quantification and spatial analysis of features in serial section images from mouse and rat brain. It aims to replicate the Quantifier feature of the Nutil software (RRID: SCR_017183) to be run locally or to be intergrated with the QUINT workflow web-tools. It builds on registration to a standardised reference atlas with the QuickNII (RRID:SCR_016854) and VisuAlign software (RRID:SCR_017978) and feature extraction by segmentation with an image analysis software such as ilastik (RRID:SCR_015246). 

For more information about the QUINT workflow:
https://quint-workflow.readthedocs.io/en/latest/ 

# Usage
As input, PyNutil requires:
1. An alignment JSON created with the QuickNII or VisuAlign software
2. A segmentation file for each brain section with the feature-of-interests displayed in a unique RGB colour (it currently accepts many image formats: png, jpg, jpeg, etc).

To run PyNutil, first fill in a test.json with the reference atlas (volume and label file) and paths to the required input files. e.g. segmentation directory and path to the alignment json (from QuickNII or VisuAlign). 

Note: The atlases available in PyNutil are listed in PyNutil/metadata/config.json.

Then Run testOOP.py to inititate the job (requires Python version 3.8 or above). 

```
from PyNutil import PyNutil

pnt = PyNutil(settings_file=r"PyNutil/test/test.json")

#Use flat can be set to True if you want to use flat files from QuickNII or VisuAlign
pnt.get_coordinates(object_cutoff=0, use_flat=False)

pnt.quantify_coordinates()

pnt.save_analysis("PyNutil/outputs/myResults")
```
PyNutil generates a series of reports saved to the "outputs" directory. 
 
# Acknowledgements
PyNutil is developed at the Neural Systems Laboratory at the Institute of Basic Medical Sciences, University of Oslo, Norway with support from the EBRAINS infrastructure, and funding support from the European Union’s Horizon 2020 Framework Programme for Research and Innovation under the Framework Partnership Agreement No. 650003 (HBP FPA).

# Developers
Harry Carey and Sharon C Yates.

# Contributors
Gergely Csucs, Ingvild Bjerke, Rembrandt Bakker, Nicolaas Groeneboom, Maja A Punchades, Jan G Bjaalie.

# Licence
GNU General Public License v3

# Related articles
Yates SC, Groeneboom NE, Coello C, et al. & Bjaalie JG (2019) QUINT: Workflow for Quantification and Spatial Analysis of Features in Histological Images From Rodent Brain. Front. Neuroinform. 13:75. https://doi.org/10.3389/fninf.2019.00075

Groeneboom NE, Yates SC, Puchades MA and Bjaalie JG. Nutil: A Pre- and Post-processing Toolbox for Histological Rodent Brain Section Images. Front. Neuroinform. 2020,14:37. https://doi.org/10.3389/fninf.2020.00037

Puchades MA, Csucs G, Lederberger D, Leergaard TB and Bjaalie JG. Spatial registration of serial microscopic brain images to three-dimensional reference atlases with the QuickNII tool. PLosONE, 2019, 14(5): e0216796. https://doi.org/10.1371/journal.pone.0216796

Carey H, Pegios M, Martin L, Saleeba C, Turner A, Everett N, Puchades M, Bjaalie J, McMullan S. DeepSlice: rapid fully automatic registration of mouse brain imaging to a volumetric atlas. BioRxiv. https://doi.org/10.1101/2022.04.28.489953

Berg S., Kutra D., Kroeger T., Straehle C.N., Kausler B.X., Haubold C., et al. (2019) ilastik:interactive machine learning for (bio) image analysis. Nat Methods. 16, 1226–1232. https://doi.org/10.1038/s41592-019-0582-9

# Contact us
Report issues here on Github or email: support@ebrains.eu
