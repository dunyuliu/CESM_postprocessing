# CESM_postprocessing

## Installation and Usage instructions

## 0. Load all necessary modules
```
module purge
ml NCL/6.6.2-foss-2018b
ml NCO/4.7.9-foss-2018b
ml netCDF/4.6.1-foss-2018b-cdf5
ml Python/2.7.15-foss-2018b
```
## 1. Clone CESM_postprocessing
```
git clone https://github.com/abishekg7/CESM_postprocessing.git
cd CESM_postprocessing
```

## 2. Install virtual environment:
```
./create_python_env -machine ada
```
## 3. Activate virtual environment:
```
ml purge 
ml  Miniconda2/4.3.21
export POSTPROCESS_PATH=<path to your CESM_Postprocessing root>
source activate $POSTPROCESS_PATH/cesm-env2
```
## 4. Create your postprocessing instance
```
create_postprocess -case [your-case-directory]
```

## Ocean Diagnostics:  
(Steps from Alper Altuntas)
## Step:1 - Edit env_postprocess.xml and env_diags_ocn.xml configuration files
*see the files in the following directory as an example:*

    /scratch/user/altuntas/g.e20.G.TL319_t13.control.001_contd

## Step:2 - Generate average files
### Step:2.1:
*Enter your project id in ocn_averages file by replacing "None" in the following line with your project id:*

    #BSUB -P None

**Note:** depending on the duration of the simulation, you may also need to increase the wallclock time.

### Step:2.2 - Submit the job:

    bsub < ocn_averages

### Step:2.3
Check the latest log file to see if averaging was completed successfully: [your-case-directory]/logs/

## Step:3 - Generate the diagnostics
### Step:3.1:
*Enter your project id in ocn_diagnostics file by replacing "None" in the following line with your project id:*

    #BSUB -P None

### Step:3.2 - Submit the job:

    bsub < ocn_diagnostics


-------------------------------------
Project repository for the CESM python based post-processing code, documentation via the wiki, and issues tracking.

The input data sets required by this code are separate from this repository. Instructions
for accessing these data sets will be coming soon. For NCAR users, the data sets are already
loaded into a central location on glade and do not need to be downloaded. 

The NCAR cheyenne and DAV quick start guide along with other documentation is available at:

http://github.com/NCAR/CESM_postprocessing/wiki/

A NCAR/CGD mailman listserv is available by user subscription to convey information to NCAR machine users
regarding the build status of common postprocessing python virtualenvs on cheyenne and geyser.

To subscribe:

http://mailman.cgd.ucar.edu/mailman/listinfo/cesm_postprocessing

To post a message to all the list members, send email to cesm_postprocessing@cgd.ucar.edu.

IMPORTANT NOTE: The purpose of the mailman listserv is to inform NCAR machine users about the build status
of the common virtualenv's on cheyenne and geyser. 

All bug reports and enhancement requests should be posted in this github repo issues and not via the mailman listserv.
