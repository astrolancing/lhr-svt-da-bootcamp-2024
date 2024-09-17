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
  - Exploration vs. Exploitation
  - RL problem formulation: Markov Decision Processes (MDPs)
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

Let's take an overview of what key concepts there are when it comes to the codebase and RL in-general. 

---

### **Week 2: Understanding and Working with Gymnasium Environments**

#### **Topics Covered:**
- Introduction to OpenAI Gymnasium
  - What is Gymnasium? (previously OpenAI Gym)
  - Overview of built-in environments (CartPole, MountainCar, etc.)
  - Interaction between agent and environment
- Working with Gymnasium environments using Python
  - Gymnasium environment API (`env.step()`, `env.reset()`, etc.)
  - Monitoring and visualizing agent performance
  
#### **Hands-On Exercises:**
1. **Exploring Gymnasium:**
   - Load a basic Gymnasium environment (e.g., CartPole).
   - Write a simple script that interacts with the environment, makes random actions, and collects rewards.

2. **Visualization with Matplotlib:**
   - Use matplotlib to plot the agent's performance over time (e.g., total reward per episode).
   - Visualize the environment using `env.render()`.

#### **Assignments:**
- Create an agent that interacts with the CartPole environment.
- Plot a graph showing the total reward per episode using matplotlib.
- Document the environment and agent interactions in a report.

---

### **Week 3: Deep Dive into Reinforcement Learning with Stable-Baselines**

#### **Topics Covered:**
- Introduction to Stable-Baselines
  - Overview of RL algorithms in Stable-Baselines (DQN, PPO, A2C)
  - Loading and training agents with Stable-Baselines
- Implementing RL algorithms in Gymnasium environments
  - Training an RL agent using the Proximal Policy Optimization (PPO) algorithm
  - Understanding the training loop and model evaluation
  
#### **Hands-On Exercises:**
1. **Training an RL Agent:**
   - Train a PPO agent on the CartPole environment using Stable-Baselines.
   - Understand and tweak hyperparameters (e.g., learning rate, gamma).
   
2. **Visualizing Training Progress:**
   - Use matplotlib to plot the agent’s performance over episodes (e.g., reward curve).
   - Evaluate the agent’s performance and compare different sets of hyperparameters.

#### **Assignments:**
- Train an RL agent using PPO on the CartPole environment and visualize the training progress.
- Experiment with different hyperparameters and analyze their impact on the agent’s performance.
- Write a short report on the challenges of training an RL agent and solutions you implemented.

---

### **Week 4: Advanced RL Concepts and Custom Environments**

#### **Topics Covered:**
- Advanced RL concepts
  - Value-based vs. Policy-based methods
  - Actor-Critic methods
  - Continuous vs. discrete action spaces
- Creating and using custom Gymnasium environments
  - Writing a custom environment for Gymnasium
  - Integrating custom environments with Stable-Baselines
- Monitoring and analyzing model performance
  - Understanding overfitting in RL models
  - Using evaluation metrics effectively
  
#### **Hands-On Exercises:**
1. **Custom Gymnasium Environment:**
   - Build and implement a custom Gymnasium environment (e.g., a simplified grid world).
   - Train an RL agent on this custom environment using Stable-Baselines.

2. **Final Project:**
   - Choose an RL algorithm (e.g., DQN or A2C) and apply it to a Gymnasium environment of your choice.
   - Implement different evaluation methods to assess the model's performance and stability.
   
#### **Assignments:**
- Create and document your own Gymnasium environment.
- Train an agent on this environment and present the results (with visualizations and explanations of the performance metrics).
- Submit a final report summarizing the bootcamp experience and lessons learned.

---

### **Bonus Topics (Optional):**
- **Distributed RL**: Introduction to advanced RL methods such as Ape-X and IMPALA.
- **Using TensorFlow/PyTorch**: Integration with RL frameworks for advanced algorithm customization.
- **RL for Robotics**: Application of RL in robotics with simulation environments like MuJoCo or PyBullet.

---

### **Deliverables:**
- Weekly assignments (code, graphs, and reports).
- Final project showcasing a trained RL agent in a custom Gymnasium environment.
- Bootcamp completion certificate based on successful completion of all assignments and the final project.

This bootcamp will offer participants a hands-on, practical approach to reinforcement learning while ensuring they gain the foundational knowledge required to apply these skills to real-world problems.