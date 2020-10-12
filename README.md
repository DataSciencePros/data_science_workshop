# Data Science Workshop

This is a broad review of how to
- do initial data analysis using pandas, and 
- create predictive models using scikit-learn and evaluating them

## Prerequisites to install before coming to the Workshop
### Option A: Docker (Recommended) (or Python and All Dependencies and Jupyter Notebook)
We will give you access to a Jupyter Notebook Server running in a virtual machine on the cloud. However, 
we recommend you to have this notebook server running in a docker image locally on your own development machine, 
so you will be able study this material later more easily.

1. Please make sure you have Docker Community Edition running on your machine.
https://store.docker.com/search?offering=community&type=edition

2. Since this is a 2GB download, preinstall the scipy-notebook, run:
```bash
docker pull jupyter/scipy-notebook:8ccdfc1da8d5
```
or `docker pull jupyter/scipy-notebook:latest` if you want to get always the latest version. (Using "latest" is not 
recommended, since you want to know which version of the platform your code was successfully running on...)   
If you would need to modify this image, like adding additional libraries, look at README.md in 
`https://github.com/DataSciencePros/scipy-notebook` for instructions about how to modify this docker image using 
Dockerfile, build and run it, and push it to dockerhub repo.

For the workshop, you will need to run one docker command (below).  
Learning docker is useful, you may want to attend the preceding workshop, or self-study:
https://github.com/DataSciencePros/docker_workshop

## Download This Repo (Data, Code and Tasks)
If you are not familiar with Git, You can browse to https://github.com/DataSciencePros/data_science_workshop, 
and click on green "Clone or Download" button, and download the zip file.

### Recommended Way: Get Them Using "git"
If new to git, you may follow this guide to install it and study:
http://rogerdudler.github.io/git-guide/ 

 [//]: # "or https://product.hubspot.com/blog/git-and-github-tutorial-for-beginners"

Make sure a git client is running on your machine, and checkout the needed repos.
if you use the commandline client:
```bash
git clone https://github.com/DataSciencePros/data_science_workshop.git
```
### Option B: Using your Computer as Jupyter Server (without Docker)
Upgrade pip, python library installer app itself
```bash
python -m pip install --upgrade pip
```

Move into project folder
```bash
cd data_science_workshop
```

Optional recommended best practice,use virtualenv, to create a clean sandbox and install all dependencies in it:
```bash
# install management tool for virtual environment directories
pip install virtualenv
# Create Virtual Environment in the local folder venv
virtualenv venv
# Activate Virtual Environment saved in folder venv
# On Windows cmd:
venv\Scripts\activate
# On Windows git bash, or on Unix-like OS:
source venv/Scripts/activate
# You will see (venv) added before your command promt
# You will type "deactivate" if you need to exit virtual environment.
```


Since this is a whirlwind tour of Data Science and NLP, the requirements are too many.
You should have only the packages you need in your requirements file...
```bash 
# install requirements in virtual environment
pip install -r requirements.txt
# start jupyter notebook
jupyter notebook
```

More on installing Jupyter:
https://jupyter.org/install

## Running the Docker Image and Viewing the Jupyter Notebooks (If you chose Option A: Docker)
Copy this repo locally in your workspace, go to (data_science_workshop) repo folder:
```bash
 # this line for recommended way above to get this repo:
 git clone https://github.com/DataSciencePros/data_science_workshop.git
 cd data_science_workshop
```
Start jupyter docker instance from this folder.

### On bash on MacOS
If using bash:
 ```bash
 docker run --rm -p 8888:8888 -e JUPYTER_LAB_ENABLE=yes \
 --mount 'type=bind,src='"$(pwd)"'/app,target=/home/jovyan/work' jupyter/scipy-notebook:8ccdfc1da8d5
 # alternative way to mount
 # mounts to a new folder, only managed by docker
 # -v "$PWD":/app
```
### On Windows
These are for running Linux Containers on Windows.
If you have selected to use Windows Containers, switch to Linux Containers by right clicking the Docker Whale in system tray:
https://docs.microsoft.com/en-us/virtualization/windowscontainers/quick-start/quick-start-windows-10

Then, you need to share the drive explicitly, going to the settings by right clicking the Docker Whale in system tray.
For screenshots, please see:
https://rominirani.com/docker-on-windows-mounting-host-directories-d96f3f056a2c

After sharing, on powershell: 
```powershell
docker run --rm -p 8888:8888 -e JUPYTER_LAB_ENABLE=yes --mount type=bind,src=$(pwd)/app,target=/home/jovyan/work jupyter/scipy-notebook:e8613d84128b
```
or on Windows command line:
```cmd
docker run --rm -p 8889:8888 -e JUPYTER_LAB_ENABLE=yes --mount type=bind,src=%cd%/app,target=/home/jovyan/work jupyter/scipy-notebook:e8613d84128b
```

### On ubuntu
Installed docker using default "Ubuntu Software Center", try the docker pull command:
```bash
docker pull jupyter/scipy-notebook:e8613d84128b
```
You may get this error:
"Got permission denied while trying to connect to the Docker daemon socket..."
Run this command in your favourite shell and then completely log out of your account and log back in (if in doubt, reboot!):

```bash
sudo usermod -a -G docker $USER
```
Then follow the MacOS section above

### Describing the Command 

Jupyter org defined this image to start notebook server serving files in /home/jovyan/work,
that is why "app" folder is mapped into that folder.
"$(pwd)" or %cd% means "print working directory" or "current directory" in shell.

- This command will (download image if local copy is not found and) create instace from image and start execution.
- It will print how to connect to the jupyter environment and load notebooks, or create new notebooks.
Paste the link to your browser.
(you may need to replace the root with localhost)
- Jupyter will show you notebooks and other files in the app folder. Clicking on one starts the notebook. 
  - For the Machine Learning workshop click on scikit_learn_workshop.ipynb
- In the notebook, clicking on one cell (code box), and shift-enter, executes code in that box.

Visiting http://localhost:8888/?token=<token> in a browser loads JupyterLab, where hostname is the name of the computer running docker and token is the secret token printed in the console. Docker destroys the container after notebook server exit, but any files written to ~/work in the container remain intact on the host.

## Running Code Snippets (cells) in the Notebook
- Select cell, click Shift-Enter
- or use "Cell" menu

## Productionizing the Model
If you want to create an web API, which will receive input, apply model to the data, and return the prediction, you can use Flask.
You may want to check use 
https://github.com/DrOzturk/FlaskZipLookupApiExample
### Credits
- Housing Data From Kaggle via Ted Petrou's Workshop: 
https://www.kaggle.com/c/house-prices-advanced-regression-techniques/data

- Workshop inspired by: 
  - Ted Petrou, https://github.com/tdpetrou/Machine-Learning-Books-With-Python
  - Ali Sivji, Joe Jasinski, Tathagata Dasgupta
  https://github.com/docker-for-data-science/docker-for-data-science-tutorial/tree/master/exercises
  https://www.youtube.com/watch?v=jbb1dbFaovg
  - Giuseppe Bonaccorso, Machine Learning Algorithms, Packt Publishing
  https://www.packtpub.com/big-data-and-business-intelligence/machine-learning-algorithms
