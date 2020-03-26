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

### 1. Let explain the pipeline step by step. 

* The function grayscale() converts the color input image into grayscale image.

![alt text][image1]

![alt text][image2]

![alt text][image3]

![alt text][image4]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
