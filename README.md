# Object-Tracking-Using-Kalman-Filter
Object Detection and Tracking using Kalman Filter


In this project, I have utilized the Kalman Filter to track a bouncing ball from a video. By estimating the position of an object from a video, provided the current position of the object, one can estimate and track the position of the object in the video with a satisfactory accuracy. 
A video is composed of a series of frames each which can be considered as a 2D signal through time. In the video used for this project, there are two types of objects, a steady object and a moving object. The steady objects do not change from frame to frame and it is assumed in this project the background scene is static. Therefore, the goal was to detect the bouncing object by subtracting out the background from each in the video. 
However, to subtract the background scene, the background scene had to be estimated from the video.  As stated above, the background doesn’t change frame to frame; as a result, the sample-mean estimator is a good estimation of the background. Therefore, to obtain an estimation of the background of the video, the average of all frames was calculated and stored as the background scene. Figure 1 below demonstrates the estimated background from the video.

![image](https://user-images.githubusercontent.com/32316270/45661142-d6343400-bac1-11e8-8921-58aa2966eb24.png)

Once, the background was extracted form the video, the bouncing ball was extracted from the video by subtracting each frame from the background. Figure 2 below indicates the result obtained from this operation for Frames 16 and 46, which are randomly chosen to better demonstrate the result.

![image](https://user-images.githubusercontent.com/32316270/45661174-eba95e00-bac1-11e8-92e1-2880b450f366.png)

Now that the position of the bouncing ball is estimated, the center of the object was calculated by inspecting the binary image of each frame and stores as the position of the moving object at each frame. In Fig. 3, it is shown that the bouncing ball is detected at each frame and the green circle denotes the detection.

![image](https://user-images.githubusercontent.com/32316270/45661198-fa901080-bac1-11e8-8125-6e19909a657c.png)

Once the position of the ball is accurately detected from the video, the Kalman ﬁlter is fed the current location of the ball to make a prediction for the next state of the system with uncertainty. Then, the Kalman algorithm was designed to compare its prediction with the received input (detected position) and correct itself upon the error. Also, for simplicity a constant velocity model was assumed in this project.
Finally, the algorithm was run to predict and track the movement of the bouncing ball with great accuracy. Figure 5 below demonstrates the prediction of the Kalman Filter with a red circle while the detection algorithm is marked green. 

![image](https://user-images.githubusercontent.com/32316270/45661238-388d3480-bac2-11e8-9a7e-b4f5f0eaf740.png)


To summarize, as it can be observed in the above figure, the Kalman Filter is a robust tool to track moving objects in a video. However, when the circumstance changes in the video, such as multiple moving objects or working with a background that constantly changes with the object of interest, it becomes much more difficult to track the object. Complicated computer vision and image processing techniques must be adapted to complement the estimation power of the Kalman Filter. 
