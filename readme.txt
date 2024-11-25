
README

Overview : This repository contains the implementation of the AR Fourier method along with comparisons to previously established methods. 
The comparison was done using both simulated and empirical datasets. We systematically compared AR Fourier to previously established 
techniques by generating simulated datasets with varying phase diffusion and noise coefficients. We also compared the method to other 
methods using a real word dataset from visual cortex of awake macaque monkey while they're performing a detection task. 


Folder structure:
      - code/
           - ARFourier_implement/
                - AR_Fourier_method.m: This repository provides an implementation of the AR Fourier method on simulated data. The code is shared 
		    as a standalone module for easy integration and adaptation by others who wish to apply the method in their own work.
                - functions/
                      - Contains functions required to run the AR_Fourier_method.m file
                      - AR_fourier_imp.m: Contains paths for FieldTrip and SLURM for parallel computing. This file may need modification to run on a 
                        different setup.
           - implement_compare/
                - Contains files which were used to implement different methods and generate results in the manuscript.
                - simulated_data/
                      - Contains scripts to implement all the phase estimation methods on all combinations of the simulated data.
                      - Contains code to compare the different methods to AR Fourier method and perform statistical analysis. 
                      - extrapolation_methods.m: Implements all the extrapolation methods for different datasets.
                      - filter_based_methods.m: Implements all the filter based methods for different datasets.
                      - echt_simdata.m: Implements the ecHT method for different datasets.
                      - simdata_comparison.m: Compares the performance of different methods using accuracy measure called PLV (Phase Locking Value)
                      - statistical_analysis.m: Run this to perform statistical analysis for the simulated dataset.
                      - result_figures.m: Run this to recreate the plots used in the result figures in the manuscript.
                      - Run simdata_comparison.m, statistical_analysis.m and result_figures.m after running all the phase estimation scripts.
                - empirical_data/
                      - Contains scripts to implement all the phase estimation methods on empirical data recorded from macaque area V4.
                      - methods_implementation.m: Implements AR Fourier and all the other phase estimation methods we wanted to compare 
                        our method against.
                      - echt_simdata.m: Implements the ecHT method in the empirical dataset.
                      - empdata_comparison.m: Compares the performance of different methods using accuracy measure called PLV and performs
                        statistical analysis. 
                - functions/ 
                      - Contains functions required to run the scripts 
                      - Some files contain paths for FieldTrip and SLURM for parallel computing which might need modification.
           - data_generation/
                - data_gen_n.py: Generates datasets similar to those used in the method implementation
      - data/
	 - simulated_data/
	       - Contains csv files for the simulated data, only data corresponding to phase diffusion of 0.001 and noise coefficient of 0.1 is provided 
                here as an example in folder freq46_11.
           - empirical_data/
	       - Contains MAT file with the recorded data from macaque area V4. 
      - results/
           - simulated_data/
                 - Contains data files in fieldtrip format and phase estimates for each of the datasets. There is one set of dataset in the folder which
                   can be used as an example to try out the code. Adding all the datasets was making the folder size large, so we have only provided 
                   one set of datsets for now. 
                 - Datasets for different phase diffusion and noise levels can be found in the 'freq46_11' folder. For example the data in 
                   'freq46_11/0.001/0.1'corresponds to a dataset with frequencies 4 Hz and 6 Hz in a 1:1 ratio, phase diffusion of 0.001 and noise 
                  	coefficient of 0.1. Only a few datasets are provided here due to space issues (data for the lowest and the highest phase diffusion
                  	is provided).  
           - empirical_data/
	        - Contains folder with processed monkey data, phase estimation results and data saved which is needed to run AR Fourier. 


Instructions:
      1. Setup : Add the code folder to the path
      2. Modify Paths:
                - Change the paths for FieldTrip and SLURM according to your setup for the files in the functions folder. Slurmfun can be cloned from 
                  the github : https://github.com/esi-neuroscience/slurmfun/tree/master
                - Update this part of the path '/add/path/to/your/folder/' to match your local setup and the location of the folder when running the 
                  code. 
      3. If SLURM is not available, modify the file to run the iterations locally. Alternatives for local execution are provided within the comment of
          the AR_fourier_imp.m file.
      4. This code can be used on any dataset after modifying the datasets into the fieldtrip format.

      
Parameters: 
      The following parameters can be adjusted in the AR_Fourier_method.m script to fit your specific data and computational resources:
           - Number of Iterations: Define how many autoregressive extrapolation iterations are performed.
           - Number of Extrapolated Samples: Set the number of samples to be extrapolated.
           - Number of Cycles for Spectral Estimation: Specify the number of cycles used during the spectral estimation process.


Notes:
      - Running Locally: If SLURM is unavailable, executing the AR extrapolation iterations locally can be very time-consuming and may require 
         significant memory.
      - Simulated Data: The example data consists of two sinusoids at 4Hz and 6Hz, with known phase values for these frequencies. Use the 
        data_gen_n.py script to generate similar datasets.


Contact: For any queries and questions, please get in touch with Shivangi Patel at shivangi.patel@esi-frankfurt.de
 
