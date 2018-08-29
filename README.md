# Data Science Workshop

This is a broad review of how to
- do initial data analysis using pandas, and 
- create predictive models using scikit-learn and evaluating them

## Prerequisites to install before coming to the Workshop
### Docker
1. Please make sure you have Docker Community Edition running on your machine.
https://store.docker.com/search?offering=community&type=edition

2. Since this is a 2GB download, preinstall the scipy-notebook, run:
```bash
docker pull jupyter/scipy-notebook:8ccdfc1da8d5
```
or `docker pull jupyter/scipy-notebook:latest` if you want to get always the latest version.   
If you would need to modify this image, README.md in `https://github.com/ATLD/scikit_jupyper_docker`
gives you instructions about how to build the same docker image from the Dockerfile and run it.

For the workshop, you will need to run one docker command (below).  
Learning docker is useful, you may want to attend the preceding workshop, or self-study:
https://github.com/ATLD/docker_workshop

## Running Notebooks
Copy this repo locally in your workspace, start instance by running docker command in (data_science_workshop) repo folder:
```bash
 git clone https://github.com/ATLD/data_science_workshop.git
 cd data_science_workshop
 docker run --rm -p 8888:8888 -e JUPYTER_LAB_ENABLE=yes \
 --mount 'type=bind,src='"$(pwd)"'/app,target=/home/jovyan/work' jupyter/scipy-notebook:8ccdfc1da8d5
 # alternative way to mount
 # mounts to a new folder, only managed by docker
 # -v "$PWD":/app
```
- It will print how to connect to the jupyter environment and load notebooks, or create new notebooks.
Paste the link to your browser.
(you may need to replace the root with localhost)
- Jupyter will show you notebooks and other files in the app folder. Clicking on one starts the notebook. 
  - For the Machine Learning workshop click on scikit_learn_workshop.ipynb
- In the notebook, clicking on one cell (code box), and shift-enter, executes code in that box.

Visiting http://localhost:8888/?token=<token> in a browser loads JupyterLab, where hostname is the name of the computer running docker and token is the secret token printed in the console. Docker destroys the container after notebook server exit, but any files written to ~/work in the container remain intact on the host.

### Download Data, Code and Study Examples
If you are not familiar with Git, You can browse to https://github.com/ATLD/data_science_workshop, and click on green "Clone or Download" button, and download the zip file.

#### Recommended Way: Get Them Using "git"
If new to git, you may study:
https://product.hubspot.com/blog/git-and-github-tutorial-for-beginners

Make sure a git client is running on your machine, and checkout the needed repos.
if you use the commandline client:
```bash
git clone https://github.com/ATLD/data_science_workshop.git
```

## Productionizing the Model
If you want to create an web API, which will receive input, apply model to the data, and return the prediction, you can use Flask.
You may want to check use 
https://github.com/DrOzturk/FlaskZipLookupApiExample
### Credits
- Housing Data From Ted Petrou's Workshop: 
https://github.com/tdpetrou/Machine-Learning-Books-With-Python
- Workshop inspired by: 
  - Ted Petrou, https://github.com/tdpetrou/Machine-Learning-Books-With-Python
  - Ali Sivji, Joe Jasinski, Tathagata Dasgupta
  https://github.com/docker-for-data-science/docker-for-data-science-tutorial/tree/master/exercises
  https://www.youtube.com/watch?v=jbb1dbFaovg
  