#**Finding Lane Lines on the Road** 

##Writeup Template

###You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

My pipeline consisted of 5 steps.
First, I converted the images to grayscale, then I applied the gaussian blur to the greyscale image to reduce the noise. Then I applied the canny edge detection algorithm. After that, I applied a filter to seperate out the region of interest where the lane lines are supposed to be and only look at that. After applying hough transform on that, we get the final output with lane lines.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by first seperating out the left and right edges of the lane lines. Then I take the bottom most point and the top most point on both the edges and join them to calculate the slope of the resulting lane line. Then extrapolating the line from the top to the bottom of the region of interest gives us a nearly accurate lane line.

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


###2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when there are no lane lines. There is currently a division by zero error in that case. Need to do better error handling.  

Another shortcoming could be when there are more than just lane lines. Separating out lanes from other noise will make sure this doesn't happen.


###3. Suggest possible improvements to your pipeline

A possible improvement would be to optimize the parameters. That will cover the second problem listed above.
Another improvement will be around how to separate lane lines from noise.
