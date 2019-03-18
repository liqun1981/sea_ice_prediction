# Getting Started

First, install git and clone the current repository

```
sudo yum install git
git clone current-repository
```

## Prerequisites

For this program we will use python 2.7.14 with packages:

```
netcdf4 1.4.3.2
numpy 1.16.2  
scipy 0.19.1
pandas 0.24.2  
scikit-learn 0.20.3 
ggplot 0.11.5  
matplotlib 2.1.2 
Cartopy 0.17.0
xarray 0.11.3 
```

## Installing 

Install python 2.7.14 and pip:

```
https://realpython.com/installing-python/
```

After python is installed run in command line

```
pip install netcdf4==1.4.3.2
pip install numpy==1.16.2  
pip install scipy==0.19.1
pip install pandas==0.24.2  
pip install scikit-learn==0.20.3 
pip install ggplot==0.11.5  
pip install matplotlib==2.1.2 
pip install Cartopy==0.17.0
pip install xarray==0.11.3 
```

## Running the program

Once the enviornment is set, and files were downloaded from readme.md data go -> open notebook and run it.


## Input 
Please go to train_test function in the notebook and change model params if custom ones are desired.

## Output
Currently the notebook will only print in the end of the process to a pandas df the 
different models that were tried and their respective loss terms. If you like to get 
the model details per latitude/longitude combination including the feature importance ->
Go to train_test function in notebook and uncomment the writing to file lines.