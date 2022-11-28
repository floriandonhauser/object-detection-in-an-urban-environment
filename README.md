# Object Detection in an Urban Environment

# Data
For this project, we will be using data from the Waymo Open dataset.

# Structure
## Data  
The data you will use for training, validation and testing is organized in the /home/workspace/data/ directory as follows:

- train: contain the training data  
- val: contain the validation data  
- test - contains 10 files to test your model and create inference videos.  


## Experiments  
The /home/workspace/experiments folder is organized as follow:  
- pretrained_model  
- reference - reference training with the unchanged config file  
- exporter_main_v2.py - to create an inference model  
- model_main_tf2.py - to launch training  
- experiment0 - create a new folder for each experiment you run  
- experiment1 - create a new folder for each experiment you run  
- label_map.pbtxt

## Prerequisites

### Local Setup

For local setup if you have your own Nvidia GPU, you can use the provided Dockerfile and requirements in the [build directory](./build).

Follow [the README therein](./build/README.md) to create a docker container and install all prerequisites.

### Download and process the data

**Note:** ”If you are using the classroom workspace, we have already completed the steps in the section for you. You can find the downloaded and processed files within the `/home/workspace/data/preprocessed_data/` directory. Check this out then proceed to the **Exploratory Data Analysis** part.

The first goal of this project is to download the data from the Waymo's Google Cloud bucket to your local machine. For this project, we only need a subset of the data provided (for example, we do not need to use the Lidar data). Therefore, we are going to download and trim immediately each file. In `download_process.py`, you can view the `create_tf_example` function, which will perform this processing. This function takes the components of a Waymo Tf record and saves them in the Tf Object Detection api format. An example of such function is described [here](https://tensorflow-object-detection-api-tutorial.readthedocs.io/en/latest/training.html#create-tensorflow-records). We are already providing the `label_map.pbtxt` file.

You can run the script using the following command:
```
python download_process.py --data_dir {processed_file_location} --size {number of files you want to download}
```

You are downloading 100 files (unless you changed the `size` parameter) so be patient! Once the script is done, you can look inside your `data_dir` folder to see if the files have been downloaded and processed correctly.
