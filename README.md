# sth_about_drone

**This repo contains little work on DJI SDK and ros of a lazybone in his senior.**

The structure of the repo is as below:

* dji_sdk_demo

  *Function*: In this package, a toy tracking result oriented gimbal control strategy is implemented. Gimbal moves so that the bounding box of the tracking is kept at the central area of the image. 
  
  *Tips*: It mimicks the original DJI_sdk_demo. So some hint might be got here...
  
  *For use*: Follow the instruction of the **DJI_sdk_read_cam** in this repo.
***

* dji_sdk_read_cam

  *Function*: In this package, the image read from the X3 camera is **cv::imshow()**ed here. Also the KCF tracker is integrated in this package for tracking the object from the abovementioned video.
  
  *Tips*: ROS Indigo stop regarding OpenCV libs as part of the ROS. Instead, it uses **cvBridge** foo converting the video stream of ROS to OpenCV video format. So if you want to use **OpenCV** handling the image from ROS, just take some time to read about **cvBridge** in ROS, which is also used in this package. The brute idea of this is subscribing the video message, then use cvBridge for converting that, the result image could be processed with OpenCV. 
  
  *For use*:
  
  Step 1 -> Refer to official DJI documentation. Specifically, it is the read_cam on Manifold. Just follow the   procedure. An namedWindow will show up.
  Step 2 -> Select the tracking object in the image with mouse. 
  Step 3 -> Run $rosrun dji_sdk_read_cam runtracker. An image with tracking algorithm running will show up. 
  Step 4 -> Refer to official DJI documentation, about how to use DJI_sdk_demo. The gimbal control demo in this repo is used the same way.
  Step 5 -> Parallel as Step 4, the distance_estimation package could be used. Details is in distance_estimation package. 
              
* distance_estimation

   *Function*: In this package, the distance between the target and the dorne is calculated. The only thing need to mention                    here is that it uses the intrinsic parameters of **X5** camera, which is quite different from **X3**. So                        **Recalibration** here is required. 
   
   *Tips*: Ask Skye for help if you have any question about this package :)
   
   *For use*: Follow abovementioned dji_sdk_read_cam instuctions until Step 3. the rosrun the only node in this package. 
