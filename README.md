## NIPS2017: Learning to Run - Environment Setup w/Jupyter Notebook

This repository contains **Windows 10 64-Bit** Instructions for participation in the NIPS 2017 Challenge: Learning to Run.

### Results
- OS: Windows 10 - "Setting Envirionmental Variables"
- Language: Python 2.7/3
- Anaconda 2
- [stanfordnmbl/osim-rl](https://github.com/stanfordnmbl/osim-rl)
- [Keras](https://keras.io/)
- [keras-rl](https://github.com/matthiasplappert/keras-rl)
- [Theano](http://deeplearning.net/software/theano/)
- [Jupyter Notebook](http://jupyter.org/)


Just going to Jump Right to the good stuff

Disclaimer: I really don't have a clue what i'm doing. This was a week of trail and error and what I ended up with....from memory

If it doesn't work, Let me know and I'll do my best to fill in the blanks

### NIPS2017: Learning to Run -  Windows 10 - 64bit - Envirionment Installation/Setup


---
**Step #1 - Visual Studio Community 2017 Workloads & Individual Components**
- [Download - Visual Studio Community 2017](https://www.visualstudio.com/thank-you-downloading-visual-studio/?sku=Community&rel=15)
    - Install
    - 2 Sections Select ALL Shown - CRITICAL STEP!
        - Workloads
        - Individual Components

![Workloads](https://github.com/Arrlin/NIPS-2017/blob/master/Environment-Setup/Workloads.jpg)
![Individual Components](https://github.com/Arrlin/NIPS-2017/blob/master/Environment-Setup/Individual_Components.jpg)

Depending On Internet Speed this could potentially take quite a while.

---


---
**Step #2 - Environmental Path Variables**
- Open Windows Search
- Type "Path"
- click "Edit the system environment variables for your account"
- Under User Variables - Select Path - Click Edit
- In Edit environment variable - Click New
- Paste "C:\Program Files\Anaconda2" - Click New
- Paste "C:\Program Files\Anaconda2\scripts" - Click OK
- [Add New Path - with Pictures](https://betanews.com/2015/11/23/windows-10-finally-adds-a-new-path-editor/)
---




---
**Step #3 - Command Prompt Work**
- Open [CMD with Admin Privileges](https://www.howtogeek.com/194041/how-to-open-the-command-prompt-as-administrator-in-windows-8.1/)
- Run the Following Commands - IN THIS EXACT ORDER!

```
c:
cd\
md LTR
cd LTR
conda create -n opensim-rl -c kidzik opensim git python=2.7
activate opensim-rl
conda install -n opensim-rl theano
conda install -c conda-forge -n opensim-rl lapack
conda install -c conda-forge -n opensim-rl keras
pip install git+https://github.com/matthiasplappert/keras-rl.git
git clone http://github.com/stanfordnmbl/osim-rl.git
pip install git+https://github.com/stanfordnmbl/osim-rl.git
conda install -n opensim-rl jupyter
python -m ipykernel install --user --name=opensim-rl
```

---

---
**Step #4 - Fixing numpy+mkl error**
Download [numpy‑1.13.3+mkl‑cp27‑cp27m‑win_amd64.whl](http://www.lfd.uci.edu/~gohlke/pythonlibs/#numpy) to "C:\LTR"

From Command Prompt:

```
c:
cd\
cd c:\LTR
activate opensim-rl
pip install numpy‑1.13.3+mkl‑cp27‑cp27m‑win_amd64.whl
```

---



---
**Step #5 - Jupyter Notebook - Workflow**

Remeber to always "activate opensim-rl" before Starting Sessions
Run the following in Commmand Prompt
```
c:
cd\
cd c:\LTR\osim-rl\scripts
activate opensim-rl
jupyter notebook
```
I'd Recommend Testing the Environment with ***"c:\LTR\osim-rl\scripts\train.arm.ipynb"***

That's It's - You Should Now be in a Jupyter Notebook Session ready to build Your "Learning to Run" R.L. Model!

---


---

**Step #6 - (Optional) Nvidia GPU Setup **
```
c:
cd\
cd C:\ProgramData\Anaconda3\envs\opensim-rl\etc\conda\activate.d
notepad keras_activate.bat
```
"Add the following Lines" to keras_activate.bat and SAVE
```
set "KERAS_BACKEND=theano"
set "THEANO_FLAGS=device=gpu,floatX=float32,lib.cnmem=.75"
```

---

Hope this was Helpful :)

James Nelson - "Arrlin"
