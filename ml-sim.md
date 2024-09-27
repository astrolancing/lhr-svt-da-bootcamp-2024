### **Reinforcement Learning Bootcamp Overview**
**Duration:** 4 Weeks 
**Level:** Beginner  
**Technologies:** Python, Gymnasium, Anaconda, Stable-Baselines, matplotlib, NumPy  
**Goals:**
- Become comfortable with Python
- Understand key concepts of reinforcement learning (RL)
- Gain practical experience in implementing RL algorithms
- Use popular RL libraries and environments (Gymnasium and Stable-Baselines)
- Visualize results and analyze agent performance using matplotlib

---

### **Week 1: Introduction to Reinforcement Learning and Setup**

#### **Topics Covered:**
- Introduction to Python and Anaconda
  - Setting up environments in Anaconda
  - Installing necessary libraries: Gymnasium, Stable-Baselines, matplotlib, NumPy
- Overview of Reinforcement Learning (RL)
  - Key concepts: Agents, Environment, Actions, Rewards, Policy, Value Function
#### **Hands-On Exercises:**
1. **Setup:**
   - Install Anaconda and set up a virtual environment.
   - Install Gymnasium, Stable-Baselines, matplotlib, and NumPy using `conda`.

2. **Basic Python and NumPy Refresher:**
   - Write simple Python scripts to get comfortable with loops, functions, and arrays.
   - Perform basic array manipulations with NumPy.

#### **Assignments:**
- Set up your Anaconda environment and install all required libraries.
- Complete exercises for Python and NumPy.

#### Assignment 0
Let's get familiar with the basics of Python, a programming language, to do some basic stuff.

First we need to install Python. We recommend [Pyenv](https://github.com/pyenv/pyenv) and [Pyenv-win]("https://github.com/pyenv-win/pyenv-win"). They are version managers for Python that allow us to have different versions.

Using Pyenv to install a recent Python version
```bash
pyenv install 3.12.5
pyenv global 3.12.5
```

Let's do some basic 'Hello, world!' stuff!
```python
# hello_world.py

def hello_world(): # <- Function definition
	print("Hello, world!") 

def hello_user(user: str): # <- define function arguments
	print(f'Hello {user}') # <- string literals allow us to embed variables

hello_world() # <- call functions
hello_user("user")
```

Let's run it! 
```bash
python hello_world.py
Hello, world!
Hello, user
```

Python is pretty readable from a no-programming experience perspective, but be careful. Python has many intricacies and possible pitfalls 
#### Assignment 1
Let's create an [environment](https://docs.python.org/3/library/venv.html), an isolated group of python dependencies and modules usually for one particular project. 
##### Why
Environments help us containerize what dependencies and modules are used by an individual project. Without environments, if you installed one version of a dependency for one project and then a different version for another project, they may end up using the wrong version. This may break things! 
##### How
Environments are often referred to as virtual environments in the Python world and can be set up using the built-in `venv` package. 

```
python -m venv venv
        ^──────^─── Tells python to run the package, i.e. 'venv' here
               └─── Arguements passed to the package, in this case again is just 'venv'
                    The first argument passed is the file directory path of the env
```

Creates the following folder structure in the given directory, we'll use `folder`
```
./folder
	- venv
		- bin
			- activate
			- ...
```

We can now 'activate' the environment in our shell environment like below though this may vary from OS to OS
```bash
source venv/bin/activate
```

We can now install dependencies without it being in our global python store using `pip`. Generally, you should always use virutal environments and refrain from installing dependencies into the global python store. 
#### Assignment 2
Anaconda is a distribution of Python. Typical Python distributions use Pip, the default package manager. Pip previously mentioned above can be used to install a variety of dependencies from PyPI (Python Package Index). Anaconda, however, provides additional registrars on top of PyPI from essentially anyone. Typically though, Anaconda is used for scientific purposes. It allows developers to easily create environments using packages, typically scientific again, not available from PyPI. We'll be using Anaconda to install various packages only available through Anaconda. 

We need to install [Anaconda](https://docs.anaconda.com/anaconda/install/) first. This varies from platform to platform. 

Unlike what was covered in Assignment 1, we'll now be using a different set of tooling from now on. Content covered in Assignment 1 was there to introduce concepts and ideas about environemnts baked-in to Python. 

Let's start with creating environments with Anaconda. This will be different compared to using `venv`
```
conda create -n ex1
             ^───── Argument that defines the name of the env, i.e. 'ex1'
```

Now we need to 'activate' the env as well. 
```
conda activate ex1
```

P.S. you can tell that you're in a Python environment if your command prompt displays the environment name before your user and hostname. This works for both `venv` and `conda` envs

Now we're all ready to use our dependencies and install new ones. The primary difference between Assignment 1 and 2 is Assignment 1 uses `pip` and the `venv` module to create environments. Assignment 2 uses Anaconda and its command-line interface (CLI) `conda`.

Let's install a common dependency, `numpy`
```
conda install anaconda::numpy
              ^────────────── Anaconda uses this syntax of owner::package
                              This can also be written, typically in older 
                              versions of Anaconda, as 'conda install -c owner package'
```

After confirming with 'y', we have now installed a package with Anaconda into our env. 

#### Assignment 3
We'll now do an introduction to `numpy`, a package dedicated to manipulating arrays, using the previous env

```python
# ex1.py

import numpy as np

a = np.arange(15)
print(a)
a = a.reshape(3, 5)
print(a)
print(a.ndim)
```
If everything is in order, you should be capable of running the python file now. 
```bash
python ex1.py
```

Let's cover what some of these functions do. `np.arange` can be used to create an in-order array of incrementing or decrementing values. There are many helper functions `numpy` provides that cover a similar role. `np.reshape` covers a key concept in `numpy` known as shape. Shape is a term used to define the dimensions of arrays and matrices. It should be clear from the output what it actually corresponds to.

'ndim' is a bit different but a common term. It refers to how many dimensions there are in a particular matrix/array. In this case we have a 2D array after reshaping it with 2 dimensions. A 3D array would have an 'ndim' of 3. 

Numpy is a powerful package with many different helper functions. We would strongly recommend becoming at least somewhat familiar with the package so that its syntax is not confusing.

#### Assignment 4
Let's set-up the actual codebase now! You will require Github access to the organization.

In a folder where you would want the codebase to be a subfolder in, run
```bash
git clone https://github.com/lhr-solar/DataAcq-PPORaceSim.git
```

cd into it
```bash
cd DataAcq-PPORaceSim
```

Follow the README.md.

If your installation runs smoothly with no issues, hurray you can now train and view models with our simulator and environment. 

Let's take a brief overview of what key concepts there are when it comes to the codebase and RL in-general. 

#### Key Concept: Machine Learning
Machine learning is the field that involves computer algorithms and programs that can solve a problem  without particular instructions. It can sometimes mimic how humans learn.

##### Reinforced Learning
A ML technique that involves a simulation and teaches the program to solve problems through trial and error. It's often used in robotics, natural language, gaming, and often self-driving cars. 

#### Key Concept: Sim-to-Real (S2R)
S2R is the concept that our simulation does not exactly mimic the real world. That's pretty obvious, but what are the implications? The model after training will be insufficent to use in the real world. The model could be completely wrong in its predictions, it could even learn to abuse our simulation in unworldly ways. The model could be slightly wrong. Its predictions could result in cumaltive error over time, resulting in large ineffencies over long times. Since we're a solar car team, endurance is the game and this is not acceptable. S2R transfer techniques help mitigate this issue by transfering sim data to real-world data. 

##### Domain Randomization

A S2R technique we employ is domain randomization. Domain randomization adds randomization the 'domain' or the data the model is trainined on. It ideally represents the randomness we may see in the real world. Bumps on the road, random bursts of wind, etc. that we cannot really model. Domain randomization also helps prevents the model from being overfitting to one particular domain. 

##### Domain Adapation

Domain adapation is a technique we plan to employ. It involves the idea that if we have enough real-world data, we can create a model that can act as a function of some input and outputs real-world data. In our case, we'd like to create a model with the following inputs, pedal position, current weather, etc. and the following output would be power draw, acceleration, velocity, etc. Domain adapation is among the most difficult techniques but can be one of the most effective at S2R.

#### Recommended Readings
- https://gymnasium.farama.org/index.html
- https://stable-baselines3.readthedocs.io/en/master/
- Reinforcement Learning: An Introduction, Second edition, Richard S. Sutton and Andrew G. Barto
  - Chapter 1
  - Reading the rest is not required, particularly Chapter 11 is applicable to us though
- https://openai.com/index/openai-baselines-ppo/


---