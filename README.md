# Assignment-14

# Midas 

MiDaS computes relative inverse depth from a single image
1. Compute depth maps for images in the input folder.
2. Run MonoDepthNN to compute depth maps.
    Args sent are : 
        input_path (str): path to input folder
        output_path (str): path to output folder
        model_path (str): path to saved model
3. Load the Network 
5. Load image and apply transforms
6. Predict and resize

## Reference url for implementation
https://github.com/intel-isl/MiDaS

## Code url
https://github.com/jai-mr/Assignment-14/blob/main/S14_CodeFinal_Midas.ipynb

## Output
https://drive.google.com/drive/folders/1L8vUdLSzy6pi7hmU97-5XGpSGuFMYl6e?usp=sharing

# PlanerCnn
1. PlaneR-CNN, detects arbitrary number of planes, and reconstructs piecewise planar surfaces from a single RGB image
2. Install Cuda 8.0
3. Install [PyTorch](https://pytorch.org/) with Cuda 8.0 support
4. Connect to Google drive to access the input data set 
5. Setup PlanerCNN
6. Instal the requirments for the needed versions
    * cffi==1.11.5
    * numpy==1.15.4
    * opencv-python==3.4.4.19
    * scikit-image==0.14.1
    * torch==0.4.1
    * tqdm==4.28.1
7. Compile nms and roialign 
   Points to be noted here are that Mask R-CNN backbone does not support cuda10.0 and gcc versions higher than 7 hence ensure that versions mentioned above are installed correctly
8. Models are saved under checkpoint.
   Model is downloaded from [here](https://www.dropbox.com/s/yjcg6s57n581sk0/checkpoint.zip?dl=0) and put it under checkpoint
9. Execute the inference code with the custom data and appropriate parameters . 
10. Please put your images (.png or .jpg files), and camera intrinsics under a folder ($customimages). The camera parameters should be put under a .txt file with 6 values (fx, fy, cx, cy, image_width, image_height) separately by a space. If the camera intrinsics is the same for all images, please put these parameters in camera.txt. Otherwise, please add a separate intrinsics file for each image, and name it the same with the image (changing the file extension to .txt). 
11. And then run: 

    python evaluate.py --methods=f --suffix=warping_refine --dataset=inference --customDataFolder=customimages

## Reference url for implementation
https://github.com/NVlabs/planercnn

## Code
https://github.com/jai-mr/Assignment-14/blob/main/S14_CodeFinal_PlanerCnn.ipynb

## Output
https://drive.google.com/drive/folders/1eQY1y0MAp_9ZihtvQ0K-7OU4BGGXkwdL?usp=sharing

# Annotated Images
The custom dataset is collected from google images for the below mentioned classes,
* hardhat
* mask
* vest
* boots

1. Used the annotation tool from https://github.com/miki998/YoloV3_Annotation_Tool to annotate the custom dataset with Bounding Boxes
2. Train the model
Parameters used,

* batch 10
* epochs 300
* images 3554
* Change the cfg/yolov3_custom.cfg parameters to wherever the below options are occuring as below
    filters=27
    classes=4

3. Execute the command as below 

    python train.py --data data/customdata/custom.data --batch 10 --cache --cfg cfg/yolov3-custom.cfg --epochs 300 --weights='weights/best.pt'


# Output images
https://drive.google.com/drive/folders/1n0XBYkrmHqg1-nliJ5Di5VQuDbyiEqGe?usp=sharing
 
