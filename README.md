# Pdm_sequenceModels_Azure

Prerequisites for this environment
* Log on to Azure
* Create a new Linux DSVM (Choose NC6 at least), this runs on GPU
* Log in via putty (or something similar)
* Run the following commands

 
First attach to a terminal for connectivity issues:
```
tmux attach -t 0
```

Environment configuration, replace `py36-mh` with your environment name: 
```
conda create -n py36-mh python=3.6
conda activate py36-mh
conda install numpy pandas matplotlib tensorflow-gpu keras h5py scikit-learn -y
conda install -c anaconda-nb-extensions nb_conda -y
conda install -c conda-forge jupyter_contrib_nbextensions -y
pip install azureml-sdk[notebooks]`
jupyter nbextension install --py --user azureml.train.widgets
jupyter nbextension enable --py --user azureml.train.widgets
```

Finally, register your kernel.  Replace Python (py36-mh) with your kernel name
```
python -m ipykernel install --user --name py36-mh --display-name "Python (py36-mh)"
```

If you want to monitor GPU while training, use this command, it is on a loop to update every second: 
``` 
nvidia-smi -l 1
```
