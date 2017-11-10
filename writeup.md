# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps:
1. Convert the image to grayscale
2. Smooth/blur the image
3. Detect edges using Canny
4. Apply image mask a set of vertices to obtain the region of interest
5. Apply Hough transform to draw lane lines


In order to draw a single line on the left and right lanes, I modified the draw_lines() function:
* Separated points into lines for left and right lanes based on slope > 0 or slope < 0 criteria
* Calculated slopes for left and right lines representing left and right lanes, respectively
* Calculated an intersection of left and right lines to converge the two lines to avoid having varying lengths of the two lines

### 2. Identify potential shortcomings with your current pipeline
I noticed at least three shortcomings where I can spend time to improve/optimize my codes:
* Calculating the intersection of left and right lines take additional processing time which was noticeable during video playback.  Optimizing this function would improve the overall speed of the program.
* During the playback of solidYellowLeft.mp4 video, I noticed that some lines show up as horizontal several times during the playback.  Although this is a split second case, I could see in real life that there's no room for this type of error with actual people insde.  I could have improved the code by calculating the standard deviation and throwing away the lines that deviate from the permitted margin of error.
* I fully expected the challenge video to not work correctly.  However, I didn't expect to see divide by zero.  In future, I would have to add unit tests to catch these types of errors in advance.

### 3. Suggest possible improvements to your pipeline

I see several areas where I would need to improve the pipeline:
* Improve the accuracy of detecting and drawing lane lines: lives depend on this.  This would probably require additonal learnings which will be provided by the course.
* Be able to dynamically identify the masking area for lane lines, and other objects in the scene.
* Spend more time in testing: again, human lives depend on this, and automated testing would be key to minimizing errors
* Identify additional scenarios: currently, this is a basic set up, and I'm sure there are many more scenarios to go through, including direct and indirect players, just like in real life.  I would love to see all the scenarios that have been identified so far whether through machine learning or manual coding, and try to come up with new scenarios that have not yet been thought of or encountered.

All in all, this has been a great introductory exercise.  I underestimated the number of hours required for the program, and I will adjust my schedules accordingly.  I also intend to re-visit the first project once I'm done with the second project to see if I can improve upon my code.
