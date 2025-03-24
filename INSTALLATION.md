### Installation
#### Note: It is recommended to run this project on a system with GPUs. Tested on windows 11 laptop with Nvidia GEFORCE RTX GPU and Apple silicon with MPS GPU.

#### Install Nvidia cuda.`https://docs.nvidia.com/cuda/cuda-installation-guide-microsoft-windows/`

#### Identify nvidia cuda version.`nvcc --version`

![cuda](images/cuda-version.png)

#### Prepare pip command to install pytorch compatible with installed cuda version.

#### Navigate to `https://pytorch.org/get-started/locally/`. In `START LOCALLY` select cuda version, OS, package type etc to get command to install.

#### Install Anaconda

#### Create conda virtual environment. `conda create --name nli_venv`
#### Activate virtual envionment `conda activate nli_venv`
#### Install dependencies using previously generated command. i.e `pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu126`
#### Install dependencies using previously generated command.i.e `pip3 install numpy pandas matplotlib scipy ipynb`
#### Run jupyter notebook. `jupyter notebook`

 