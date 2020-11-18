# JupyterHub-Instructions

JupyterHub was installed using this tutorial: [Note: JupyterHub with JupyterLab Install using Conda](https://www.pugetsystems.com/labs/hpc/Note-JupyterHub-with-JupyterLab-Install-using-Conda-1729/?__cf_chl_captcha_tk__=2b09eabaee415536161c510f692993167f0fae39-1605719268-0-AT0lMwu6Nq5_klECiVLrHm1lSOYR-Xgj_p1h1z3SMHWZOxNAcNFfcA81gy-W3c0EehzlXvCeEFzl_7_z6j8qyfCJVgMVOQAZZxtTQPeSWVNM-fG1edis8D9um7_Z6BktMeetiFSG1Jr9c9U0uSEKvT3_TXkt7twDIlpr_CuHtjcRiYqrI1HkBt5Bo67anv-wnfd38uAcc8byWJBvo06rPWG0E-hN11QlIGbzYBZAgSLUJqYxPyndkYx9lHV3BUmL33DQMpJVeKJ09dQRIg39MjEohMt7K_jNA47m_nUoQQEVaFqGgZzHejzEBZ-pLHZoy0CElaEbuGnLji2QOS7Eo9Ewp7pVj7Aap4U8a9ApuvyVS_9OeBPE0q8_hnKrXIDz4YEzaKcDmgXewLoTVy9XwIrg4JSDK7x8RM1DsmUV5Z4vFNuejxyA5hlb5wJ1PB3UAAt8klMkqEoCIk8mUWnwFHRgp0nQ5sb7tp3XiXcKVn9kiG4J-51Ld-tzk6hNYHHXcmT4Vc215MpftE_YKQo0VkyiVmaX5YHnBX5kwPwyI1eoetEPC_zRL8HNyHFaRUejGkcem3kaUdlFulI7wpRvemudlphsn9MDUGogeY9zfWby)


There are both JupyterLab and Jupyter Notebook installed on the server. Just change *tree* and *lab* in the end of url (*tree* for Jupyter Notebook, *lab* for JupytherLab). There is [post](https://www.analyticsvidhya.com/blog/2020/06/10-powerful-reasons-jupyterlab-data-science/) about 10 reasons to move to JupyterLab. 

## How to install python packages

### In Jupyter Notebook (in cell)
Best way:
```
import sys
!{sys.executable} -m pip install numpy
```
Not recomended (because it will install package to **Python3** kernel:
```
!pip install numpy
```
