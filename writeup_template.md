# **Finding Lane Lines on the Road** 

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Read a color image
* Convert the color image into grayscale image
* Apply Gaussian blurring to smooth the image
* Apply Canny edge filter to find edges in the image.
* Convert Canny edge image into Hough space to find lines.
* Set up threshold values t find long lines.
* Create a region of interest in which lanes to be found.
* Join the dotted lanes in one single line.


[//]: # (Image References)

[image1]: ./test_image_output/gray.png "Grayscale"
[image2]: ./test_image_output/blur.png "Blur Image"
[image3]: ./test_image_output/canny_edge.png "Canny Edge Image"
[image4]: ./test_image_output/output.png "Output"

---

### Reflection

### 1. Lets explain the pipeline step by step. 

* The function grayscale() converts the color input image into grayscale image.
![alt text][image1]

* The function gaussian_blur() smooths the grayscale image as shown below.
![alt text][image2]

* The function canny() finds edges in the smoothed grayscale image as shown below.
![alt text][image3]

* The function hough_lines() converts the Canny edge image into Hough space and calls the function draw_lines().

* Inside the draw_lines() function a logic is implemented to draw just one extended line for the right and left lanes instead of dotted lanes. The logic behind this implementation is as explained below.

  * It is possible to separate lane lines belonging to left lane and right lane as the slope is positive for right lanes and it is negative for left lanes.

  * Use the function np.polyfit() to find least squares polynomial fit for the left and right lanes.

  * The function np.poly1d() then finds one-dimensional polynomial class for each lane. 

  * This helps to find x-cordinates of start and end points of the left and right lanes.

  * The start and end y- coordinate points for both left and right lanes are same since both the lanes start from bottom of the image and end just below the horizon.

  * This way the lines are extended and drawn transparently on the input color image.  

* Finally, the result onto the input color image as shown below.

![alt text][image4]

### 2. Identify potential shortcomings with your current pipeline

* Lanes are not detected sometimes. The main reason is the color of lanes and changing lightening conditions


### 3. Suggest possible improvements to your pipeline

* Consideration of color of lanes.
* Lanes that are not straight (curvy lanes) needs special implementation.
