# Finding Lane Lines on the Road
## Writeup
---
### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.
In order to complete with the project targets, it was created 3 similar functions that were called as: line_recognition(), line_recognition2(), and line_recognition3(). In following lines is described in detail each of these functions.

#### line_recognition()

This is the master pipeline that is consisted of the next steps:
- Transformation of raw image to grayscale
- Defining a kernel size and apply Gaussian smoothing
- Defining parameters for Canny
- Creating masked edges image using region_of_interest function
- Defining the Hough transform parameters
- Draw the lines on the edge image


My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I .... 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...

This repository has the notebook used to solve finding lane lines project
