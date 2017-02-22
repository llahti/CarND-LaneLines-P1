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
[image9]: ./images_for_writeup/proposed_roi.jpg "New proposed ROI"


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

####3. Detect Edges From Image
Before we can detect lines from image we need to detect edges. Edge detection produces following type of image.
![Edges Detected][image5]

####4. Define Region of Interest
This step is also needed before detecting lines, because we are only interested in finding lines from the area from which we're able to find lane lines. If we don't define ROI then our lane detection detects all possible lines.
![Define Region Of Interest][image6]


####5. Detect Lines
Now is time to detect lines from image. Our image is already in condition that most probably we are able to find lane lines.
We are using hough transformation to detect lines from image.
From image we can see that there are quite few lines found and we take care of those on next step.
![Lines Detected][image7]

####6. Line Extrapolation and Averaging
This step reduces all lines to left and right lines as seen in image below.
This is done by first sorting lines to left and right pairs.
Then extrapolating those to extend from apex to bottom of image.

![Line Extrapolation and Averaging][image8]

####7. Line averaging
Then  lines are averaged and for video stream there is rolling average filter to reduce line shaking.

####7. Augment to Image or Video Stream
Averaged lines are then augmented to image/video stream. Basically it is just to combining the original image with image which contains extrapolated and averaged lines.

![Annotated Image][image2]


###2. Identify potential shortcomings with your current pipeline

There are several shortcomings what i could think of.
- Sensitivity to lighting changes within image
- If lane lines are close to the road edge then it is highly possible that the road edge will de detected as well
- Objects such as cars or road markings within region of interest could mess up line detection
- Highly curved lane markings could be ignored by algorithm
- Rolling average algorighm can't handle "null" values

As we can see from the challenge video this current pipeline is not working reliably and needs modifications.

###3. Suggest possible improvements to your pipeline

- Pipeline should be better on adapting to changing lighting conditions
- Defining ROI in fine details
![Proposed ROI definition][image9]
- Also would be nice if ROI could be adjusted on the fly
- Detect which areas are outside of the road
- Also there could be possibility to use color information to make pipeling better on adapting different conditions
- Contrast and brighness modifications could be tried as well.

