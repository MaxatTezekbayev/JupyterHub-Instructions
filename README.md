# JupyterHub-Instructions

JupyterHub was installed using this tutorial: [Note: JupyterHub with JupyterLab Install using Conda](https://www.pugetsystems.com/labs/hpc/Note-JupyterHub-with-JupyterLab-Install-using-Conda-1729/?__cf_chl_captcha_tk__=2b09eabaee415536161c510f692993167f0fae39-1605719268-0-AT0lMwu6Nq5_klECiVLrHm1lSOYR-Xgj_p1h1z3SMHWZOxNAcNFfcA81gy-W3c0EehzlXvCeEFzl_7_z6j8qyfCJVgMVOQAZZxtTQPeSWVNM-fG1edis8D9um7_Z6BktMeetiFSG1Jr9c9U0uSEKvT3_TXkt7twDIlpr_CuHtjcRiYqrI1HkBt5Bo67anv-wnfd38uAcc8byWJBvo06rPWG0E-hN11QlIGbzYBZAgSLUJqYxPyndkYx9lHV3BUmL33DQMpJVeKJ09dQRIg39MjEohMt7K_jNA47m_nUoQQEVaFqGgZzHejzEBZ-pLHZoy0CElaEbuGnLji2QOS7Eo9Ewp7pVj7Aap4U8a9ApuvyVS_9OeBPE0q8_hnKrXIDz4YEzaKcDmgXewLoTVy9XwIrg4JSDK7x8RM1DsmUV5Z4vFNuejxyA5hlb5wJ1PB3UAAt8klMkqEoCIk8mUWnwFHRgp0nQ5sb7tp3XiXcKVn9kiG4J-51Ld-tzk6hNYHHXcmT4Vc215MpftE_YKQo0VkyiVmaX5YHnBX5kwPwyI1eoetEPC_zRL8HNyHFaRUejGkcem3kaUdlFulI7wpRvemudlphsn9MDUGogeY9zfWby)


There are both JupyterLab and Jupyter Notebook installed on the server. Just change *tree* and *lab* in the end of url (*tree* for Jupyter Notebook, *lab* for JupytherLab). There is [post](https://www.analyticsvidhya.com/blog/2020/06/10-powerful-reasons-jupyterlab-data-science/) about 10 reasons to move to JupyterLab. 

## How to install python packages

### In Jupyter Notebook (in cell)
Not recomended (because it will install package only to **Python3** kernel):
```
!pip install numpy
```
Best way (because it will install package to the current kernel of notebook):
```
import sys
!{sys.executable} -m pip install numpy
```
Note: when you install package to some kernel, the same kernel of other users will not be modified (it is also true for installation using terminal).

### In terminal
if you want to install package to **Python3** kernel:
```
pip install numpy

or 

python -m install numpy
```

if you want to install package to other kernel, first list all enverinments (*jupyterhub* environment refers to **Python3** kernel):
```
conda env list
```
```
conda activate pytorch1.6 
pip install numpy
```
In order to deactivate conda environment:
```
conda deactivate
```
To check which python or pip you use:
```
which python
which pip
```

## Create your own environment via conda:
```
conda create --name py3.6 python=3.6 
```
"python=3.6" will install python3.6. The name of the environment will be "py3.6". In the end of the command, you can add names of packages (optional: conda create --name py3.6 python=3.6 numpy pandas gensim). Note: it will not create new python kernel. In order to add kernel with this environment (to use it in Jupyter Notebook), run:
```
conda activate py3.6
pip install ipykernel
python -m ipykernel install --user --name "py3.6" --display-name "Python 3.6"
```
Note: it will create environment and kernel only for you, other users will not see it and will not be able to use it.
If you want to delete your environment:
```
conda deactivate
conda env remove --name py3.6
```

## Other conda commands
There is [Conda CHEAT SHEET](https://docs.conda.io/projects/conda/en/4.6.0/_downloads/52a95608c49671267e40c689e0bc00ca/conda-cheatsheet.pdf). Or you can google it.

## Choose specific GPU to run python script:
in terminal:
```
CUDA_VISIBLE_DEVICES 0 python script.py
```
in Jupyter Notebook:
```
import torch
import os
os.environ["CUDA_DEVICE_ORDER"]="PCI_BUS_ID"
os.environ["CUDA_VISIBLE_DEVICES"]="1"
```
or 
```
import torch
torch.cuda.set_device(1)
```
## Run multiple python scripts simultaneously:
```
python script1.py &
python script2.py --flag 1 --other_flag 2 &
python script3.py
```
You also can specify GPU for each script:
```
CUDA_VISIBLE_DEVICES 0 python script1.py &
CUDA_VISIBLE_DEVICES 0 python script2.py --flag 1 --other_flag 2 &
CUDA_VISIBLE_DEVICES 1 python script3.py
```

