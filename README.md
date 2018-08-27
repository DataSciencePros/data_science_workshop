# Data Science Workshop

This is a broad review of how to
- do initial data analysis using pandas, and 
- create predictive models using scikit-learn and evaluating them

## Prerequisites
### Docker
1. Please make sure you have Docker Community Edition running on your machine.
https://store.docker.com/search?offering=community&type=edition

2. Copy the dockerfile from `https://github.com/ATLD/scikit_jupyper_docker`
and follow the instructions in README.md there to build the docker image and run it.

If you are new to docker, you may want to attend the preceding workshop, or self-study:
https://github.com/ATLD/docker_workshop

#### Running Notebooks
Copy this repo locally in your workspace, start instance by running docker command in (data_science_workshop) repo folder:
```bash
 git clone https://github.com/ATLD/data_science_workshop.git
 cd data_science_workshop
 docker run -p 9999:8888 \
--mount 'type=bind,src="$(date)"/app,target=/app' mlnb
```
- It will print how to connect to the jupyter environment and load notebooks, or create new notebooks.
Paste the link to your browser.
(you may need to replace the root with localhost)
- Jupyter will show you notebooks and other files in the app folder. Clicking on one starts the notebook. 
  - For the Machine Learning workshop click on scikit_learn_workshop.ipynb
- In the notebook, clicking on one cell (code box), and shift-enter, executes code in that box.

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
You can use 
https://github.com/DrOzturk/FlaskZipLookupApiExample
### Credits
- Housing Data From Ted Petrou's Workshop: 
https://github.com/tdpetrou/Machine-Learning-Books-With-Python
- Workshop inspired by: 
  - Ted Petrou, https://github.com/tdpetrou/Machine-Learning-Books-With-Python
  - Ali Sivji, Joe Jasinski, Tathagata Dasgupta
  https://github.com/docker-for-data-science/docker-for-data-science-tutorial/tree/master/exercises
  https://www.youtube.com/watch?v=jbb1dbFaovg
  