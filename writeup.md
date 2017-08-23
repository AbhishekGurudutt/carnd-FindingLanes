
**Finding Lane Lines on the Road**

[//]: # (Image References)

[image1]: ./writeup/gray_image "Grayscale"
[image2]: ./writeup/gaussian_blur_image "Gaussian Blur"
[image3]: ./writeup/canny_image "Canny"
[image4]: ./writeup/roi_image "Region of Interest"
[image5]: ./writeup/hough_image "Hough Transform"
[image6]: ./writeup/overlayed_image "Overlayed Image"

---

### Reflection

### 1. Pipeline of preprocessing and drawing lines.

My pipeline consists of 6 steps.

1. I converted the images to grayscale:
![alt text][image1]

2. Grayscale images are blurred using gaussian blur function ,with kernel size of 7:
![alt text][image2]

3. Blurred images are passes through canny function to detect the edges:
![alt text][image3]

4. Detected edges are then filtered according to the defined Region of Interest:
![alt text][image4]

5. Images with filtered edges are passed to Hough Transform and draw lines function:
![alt text][image5]

6. Obtained lines are then overlayed on the initial images:
![alt text][image6]

Function draw_lines() draws a single line on the left and right lanes. Once the coordinates was passed from hough transform to draw_lines(), slope for each line was calculated and was classified as left line or right line according the slope angle. Right and left slope angles were averaged. The farthest coordinate on the line from the base of image was noted. These coordinates and slope was used to determine the coordinate on the lower end of the image. A straight line was drawn to connect the determined coordinates.


### 2. Potential shortcomings with current pipeline

With the current pipeline there were a few shortcomings that were observed,

1. In video, the lines are not steady.

2. The lines sometime overshoots and is drawn outside of the road.

3. If there is a curved road, the pipeline does not work.


### 3. Possible improvements to the pipeline

A possible improvement would be to

1. Store the previous state of the lines and apply a smoothening filter.

2. Have a check and limit the draw line to a defined pixel value.

---
