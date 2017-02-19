**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


### Reflection

The pipeline I used contains 5 steps.
  - Convert image to HLS space and apply thresholds to leave only the required data;
  - Apply gaussian blur to smooth the noise;
  - Run canny to find the edges of the objects on the picture;
  - Apply mask to clean everything except the region of interest;
  - Apply Hough transform to the resulting image
  - Draw lines based on Hough transform findings

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by including several steps. First, the lines are divided by slope to left and right. Meanwhile, they are thresholded by the slope, so some wrong directed line would not fit there. Then the filter by the position on the image is applied. Therefore, I receive list of points of left and right lines. Then using the `cv2.polyfit()` function, the resulting line is fit there and interpolated to the boundaries of the region of interest.

###2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when the line is interrupting, so Hough transform might find the wrong points and connect them improperly, which would result in unexpected line shift.

Another shortcoming could be the color form, so the filters I applied will not detected required information about lines, as currently the are optimized to fit to the given videos.


###3. Suggest possible improvements to your pipeline

A possible improvement would be to experiment with parameters of Hough transform and Canny to improve detection of potential line sections and proper interconnection later.

Another potential improvement could be to experiment with color spaces and filters to improve thresholding which could make it work in other conditions(different daytime, weather conditions, etc)
