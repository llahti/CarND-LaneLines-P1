#**Finding Lane Lines on the Road** 

##Writeup
---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report
* Briefly the goal is to annotate video with lane marks


[image1]: ./test_images/solidWhiteCurve.jpg "Original image"
[image2]: ./test_images/solidWhiteCurve_7_final.jpg "Annotated Image"
[image3]: ./test_images/solidWhiteCurve_1_grayscale.jpg "Grayscaled Image"
[image4]: ./test_images/solidWhiteCurve_2_blurred.jpg "Blurred Image"
[image5]: ./test_images/solidWhiteCurve_3_edges.jpg "Edged detected"
[image6]: ./test_images/solidWhiteCurve_4_roi.jpg "Region of Interest Defined"
[image7]: ./test_images/solidWhiteCurve_5_houghlines.jpg "Lines Detected"
[image8]: ./test_images/solidWhiteCurve_6_extrapolated.jpg "Lines Averaged and Extrapolated"


**Original Image**
![Original Image][image1]
**Annotated Image**
![Annotated Image][image2]

---

### Reflection

###1. Pipeline Description

My pipeline is bit modified version of suggested pipeline as i have created few extra functions to help on task.
Anyhow the general principle should follow quite well the suggested principle. Below is description of pipeline step by step.

Starting point is the original image such as 
![Original Image][image1]

####1. Convert image to grayscale
First step is to convert image to grayscale as it will make image processing faster and it is easier to apply different type of image manipulation techniques. 
![Image converted to grayscale image][image3]

####2. Smooth Image
In order to get rid of small anomalies in image it is better to smooth it certain amount. I used kernel size 9 for smoothing.
Resulting image looks bit blurred (as it should) and from that we are able to find edges.
![Smoothed Image][image4]


---
My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I .... 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


###2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


###3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
