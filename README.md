Tensorflow and its subsidiaries are very finicky with how versions like to cooperate with your hardware.
Follow below steps:

1. Install anaconda from [https://www.anaconda.com/download/success](url), make sure you add this to path during setup process.
2. Install CUDA 11.2 from [https://developer.nvidia.com/cuda-11.2.0-download-archive?target_os=Windows&target_arch=x86_64&target_version=10&target_type=exelocal](url), Windows 10 local version runs fine on Windows 11
3. Install cuDNN 8.1.1, cuDNN Library for Windows (x86), from [https://developer.nvidia.com/rdp/cudnn-archive](url)
4. Open cuDNN zip directory, copy all contents inside each corresponding folder to matching folder in C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.2
   e.g. all files from cuDNN lib should be copied into the lib folder inside the addressed directory, etc.
5. Search for environment variables in your system's settings app; click edit environment variables; in the bottom right portion of the pop-up, click on the 'Environment Variables' button; click on path and edit in the top half of new popup
6. Click 'New' and copy paste the three addresses below indivually before hitting 'OK':
   C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.2\bin
   C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.2\libnvvp
   C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v11.2\extras\CUPTI\lib64
7. Create virtual environment with Conda and create kernel for use in jupyter lab in command terminal:
   conda create -n venv_name python==3.9
   conda activate venv_name
   pip install jupyter
   pip install ipykernel
   python -m ipykernel install --name=venv_name
8. In terminal, run lines:
   conda install -c conda-forge cudatoolkit=11.2 cudnn=8.1.0
   python -m pip install "tensorflow<2.11"
   pip install cv2 matplotlib numpy==1.26.4 pandas

All dependencies should be sorted at this point in time, make sure the selected kernel in the top-left of the screen in jupyter lab matches the name set in step 7.
