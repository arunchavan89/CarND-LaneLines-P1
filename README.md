# **Finding Lane Lines on the Road** 
[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)

<img src="examples/laneLines_thirdPass.jpg" width="480" alt="Combined Image" />

Overview
---

When we drive, we use our eyes to decide where to go.  The lines on the road that show us where the lanes are act as our constant reference for where to steer the vehicle.  Naturally, one of the first things we would like to do in developing a self-driving car is to automatically detect lane lines using an algorithm.

In this project you will detect lane lines in images using Python and OpenCV.  OpenCV means "Open-Source Computer Vision", which is a package that has many useful tools for analyzing images.  

To complete the project, two files will be submitted: a file containing project code and a file containing a brief write up explaining your solution. We have included template files to be used both for the [code](https://github.com/udacity/CarND-LaneLines-P1/blob/master/P1.ipynb) and the [writeup](https://github.com/udacity/CarND-LaneLines-P1/blob/master/writeup_template.md).The code file is called P1.ipynb and the writeup template is writeup_template.md 

To meet specifications in the project, take a look at the requirements in the [project rubric](https://review.udacity.com/#!/rubrics/322/view)

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

The Project
---

## If you have already installed the [CarND Term1 Starter Kit](https://github.com/udacity/CarND-Term1-Starter-Kit/blob/master/README.md) you should be good to go!   If not, you should install the starter kit to get started on this project. ##

**Step 1:** Set up the [CarND Term1 Starter Kit](https://github.com/udacity/CarND-Term1-Starter-Kit/blob/master/README.md) if you haven't already.

**Step 2:** Open the code in a Jupyter Notebook

You will complete the project code in a Jupyter notebook.  If you are unfamiliar with Jupyter Notebooks, check out [Udacity's free course on Anaconda and Jupyter Notebooks](https://classroom.udacity.com/courses/ud1111) to get started.

Jupyter is an Ipython notebook where you can run blocks of code and see results interactively.  All the code for this project is contained in a Jupyter notebook. To start Jupyter in your browser, use terminal to navigate to your project directory and then run the following command at the terminal prompt (be sure you've activated your Python 3 carnd-term1 environment as described in the [CarND Term1 Starter Kit](https://github.com/udacity/CarND-Term1-Starter-Kit/blob/master/README.md) installation instructions!):

`> jupyter notebook`

A browser window will appear showing the contents of the current directory.  Click on the file called "P1.ipynb".  Another browser window will appear displaying the notebook.  Follow the instructions in the notebook to complete the project.  

**Step 3:** Complete the project and submit both the Ipython notebook and the project writeup


