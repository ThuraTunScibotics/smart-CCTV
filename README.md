# smart-CCTV

## Introduction
Normally, most cases of CCTV just record all times situations and store video data into storage-drive or actively watching by human. As CCTV is used to watch or check unormal and dangerous activities happening in the places like shops, supermarkets or locations that stored precious goods, so it is better to know the situations immediately if unnormal or illegal activities are happening. For the case like a group of thives try to enter and steal things from a shop during midnignt when nobody is at the shop. At this time, something changes and movements of them will appear in front of CCTV's view. If CCTV is the purpose for just recording and storing data for checking later, it would be less probability for catching the illegal group as fast as possible. In this case, it would be great there is a software in CCTV that can detect something changes and activites happening in camera's view, and sending allert to someone authority or owner. 
In this project, we will record those specific changes or activities and just storing the video clip with changes or activities into storage-media for saving much storage space. Whenever the changes are happen, we just store the frame with object detection of that significant changes, and this make our CCTV more smarter. We can also send this video clip to owner or autority as CCTV alert-system. You can see the two situations of normal condition and significant unnormal activities happened in the shop by seeing the following images.

<img src="/video-data/cctv-normal.png" height="40%" width="40%" alt="CCTV view with normal condition" title="Do not save the frames in the storage">  <img src="/video-data/cctv-changes.png" height="40%" width="40%" alt="CCTV view with the thives enter the shop" title="Save the frames when changes happen">

## Data
#### Use sequeces of frames streamed by CCTV
* [human-and-car-cross-the-train](https://github.com/ThuraTunScibotics/smart-CCTV/tree/main/video-data/GroundtruthSeq/RawImages)
* [car-people-on-the-road-campus](https://github.com/ThuraTunScibotics/smart-CCTV/tree/main/video-data/Campus)
* [shopping-mall](https://github.com/ThuraTunScibotics/smart-CCTV/tree/main/video-data/ShoppingMall_resized)

## Packages Requirements
Check the package manager, [conda](https://docs.conda.io/projects/conda/en/latest/index.html) which will be required to install required libraries & packages under specific virtual environment.
Install anaconda on your machine, and run the following cell on terminal/command prompt after installed.
```
conda create -n SmartCCTV

conda install jupyter python opencv matplotlib numpy

pip install cvlib
```
## Algorithms of the system
1. Background Subtraction for foreground image by using Gaussian mixture based background/foreground subtraction function
   (Background-subtraction is better than frame-diferencing for better estimation of changes)
2. Denoising using Morphology operation with OpenCV
3. Extract Connected Components using OpenCV, and that components are frame-with-changes
4. Take object detection on frame-with-changes
   (cvlib uses YOLOv3 model trained on COCO dataset capable of detecting 80 common objects in context)
6. Save these changes frame and object detected frames using cvlib library
7. Display and view these saved changes-frames

## Demo & Step-by-step

**Here is the comparison of *input frame [left]* and the *final resultant output frame [right]*, achieved by saving just significant chages from the input frame with image processing and computer vision algorithm and apply YOLOv3 object detection to the frame. This can save alot CCTV storage and make more smarter.**
<img src="https://github.com/ThuraTunScibotics/smart-CCTV/blob/main/resultant-data/input-train-cross.gif" height="40%" width="40%">                          <img src="https://github.com/ThuraTunScibotics/smart-CCTV/blob/main/resultant-frame-changes-videos/train-cross.gif" height="40%" width="40%">


The following outputs are the results of each step:

**Original input frame**

<img src="https://github.com/ThuraTunScibotics/smart-CCTV/blob/main/resultant-data/input-train-cross.gif" height="50%" width="50%">


Step-1: After **subtracting background for foreground image** frame having with noise

<img src="https://github.com/ThuraTunScibotics/smart-CCTV/blob/main/resultant-data/noise-result.gif" height="50%" width="50%">


Step-2: After **denoising** nioses from frame

<img src="https://github.com/ThuraTunScibotics/smart-CCTV/blob/main/resultant-data/denoised-result.gif" height="50%" width="50%">


Step-3: After **extracting only connected components/features** from the frame

<img src="https://github.com/ThuraTunScibotics/smart-CCTV/blob/main/resultant-data/component-seq1.gif" height="50%" width="50%">


Step-4: After **taking object detection and saving frames-with-changes**

<img src="https://github.com/ThuraTunScibotics/smart-CCTV/blob/main/resultant-frame-changes-videos/train-cross.gif" height="50%" width="50%">


## Future Work

## References

