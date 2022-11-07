# How to run funMotifs
The current git version of the pipeline can be found in Rackham at 
/proj/snic2020-16-187/nobackup/funMotifs_analysis/funMotifs
## Interactive command (being in funmotifs/src)
python3 funMotifsMain.py --param_file='../conf/main_parameters_hg19.conf' --temp_dir='tmp' --force_overwrite=true\
Highly recommend to safe shell output and error in files (i.e., using > and 2>)
## necessary packages/modules
PostgreSQL: module load PostgreSQL\
Python packages that might need installation:
 * pybedtools
 * pathos
 * psycopg2
 * statsmodels

My way:
 * use conda environment (Miniconda or Anaconda)
 * check whether package is available
 * install package using conda (search (google) for 'conda install *package_name*')\
--> compare with src/funCall.bashrc

## data files
Data files are specified in conf/main_parameters.conf (small data set) or conf/main_parameters_hg19.conf (bigger data
set)\
The most recent downloads from the databases are the data_tracks specified in conf/main_parameters_hg19.conf

## further notes
At the moment there is a bug while starting the database from the pipeline. It is best to delete the directory *database*
and *logfile* before running the tool.\
You will have to specify the database user name in the conf/main_parameter* file. The user name should be your user name
for the server.

## sbatch command
The slurm command I used to run the tool is:\
sbatch -A snic2022-5-189 -n 6 -t 24:00:00 funCall.bashrc\
Best to read the manual before using it. -t can be up to 10 days (240:00:00). It is best to use this as setting when you
run the tool on large data without knowing the runtime.