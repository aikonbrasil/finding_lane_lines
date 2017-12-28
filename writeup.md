# Finding Lane Lines on the Road
## Writeup
---

[//]: # (Image References)

[imag1]: ./pictures_red_lines/1.png "picture 1"
[imag2]: ./pictures_red_lines/2.png "picture 2"
[imag3]: ./pictures_red_lines/3.png "picture 3"
[imag4]: ./pictures_red_lines/4.png "picture 4"
[imag5]: ./pictures_red_lines/5.png "picture 5"
[imag6]: ./pictures_red_lines/6.png "picture 6"

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.
In order to complete with the project targets, it was created 3 similar functions that were called as: line_recognition(), line_recognition2(), and line_recognition3(). In following lines is described in detail each of these functions.

#### line_recognition()

This is the master pipeline that is consisted of the next steps:
- Transformation of raw image to grayscale using grayscale(img) helper function
- Defining a kernel size and applying Gaussian smoothing using the gaussian_blur(img, kernel_size) helper function
- Defining parameters for Canny using canny(img, low_threshold, high_threshold) helper funtion
- Creating masked edges image using region_of_interest helper function 
- Defining the Hough transform parameters using hough_lines(img, rho, theta, threshold, min_line_len, max_line_gap) helper function. This hough_lines function plot the lines using the draw_lines(img, lines, color=[255, 0, 0], thickness=2) helper function.
- Draw the lines on the edge image

The next pictures are result of the pipeline described before:

![alt text][imag1] ![alt text][imag2]

![alt text][imag3] ![alt text][imag4]

![alt text][imag5] ![alt text][imag6]

The videos that were generated for raw lines detected with Hough Tranform could be located in the next links:

[Video_Raw Lines_SolidWhiteRight](https://github.com/aikonbrasil/finding_lane_lines/blob/master/video_raw_lines/solidWhiteRight_raw_lines.mp4)

[Video_Raw Lines_SolidYellowLeft](https://github.com/aikonbrasil/finding_lane_lines/blob/master/video_raw_lines/solidYellowLeft_raw_lines.mp4)

### line_recognition2()

This function is an optimization of line_recognition() function, this optimization was done in order to achieve target defined for video detection line(right_side road lines and yellow_left_side road lines). Basically we added a new pipeline to the function draw_lines(). It was saved with the name draw_lines2(). draw_lines2() is characterized by the next features:
- Calculating slope and intersection for every line that was identified by Hough transform.
- Lines are clusterized in two groups: left_lines and right_lines, it was done using the slope information.
- In order to decrease noise in slope and intersection, we used a filter based on mean and standard deviation metrics that correspond to every line indentified in each frame. This metrics where used to filter lines that follow the next rule: mean(slope)-slope < std(slope). In this case mean(slope) is the mean of all lines detected by Hough transform in actual frame, slope is metric that corresponds to the an specific line that is being evaluated, and std(slope) is the standard deviation of all slopes detected in actual frame.
- In order to take advantage of old information of previous frames, it was applied a weight average between actual slope and intersection. For example, in the case of the slope we considered the next relationship: mean_m_right = np.mean(vector_m_right)*0.2 + m_history_right*0.8. In this case we priorized history information of previous frames.

The videos generated in order to follow P1 requirements could be located in the next links :

[Video_P1 Lines_SolidWhiteRight](https://github.com/aikonbrasil/finding_lane_lines/blob/master/video_P1/solidWhiteRight_SolidLine.mp4)

[Video_P1 Lines_SolidYellowLeft](https://github.com/aikonbrasil/finding_lane_lines/blob/master/video_P1/solidYellowLeft_SolidLine.mp4)

### line_recognition3()

In order to achieve the challenge, we inserted extra modifications to line_recognition2() function. The features that were added are:
- Filtering slopes that are near zero, in order to avoid horizontal verticals that are abundant in the video challenge.
- Using some exceptions in cases in which some variables generate NaN values.

The videos generated in order to follow Challenge P1 project could be located in the next links :

[Video_P1_Challenge](https://github.com/aikonbrasil/finding_lane_lines/blob/master/video_P1/challenge_SolidLine.mp4)


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...

This repository has the notebook used to solve finding lane lines project
