# **Finding Lane Lines on the Road** 
## ZHAN YUAN
## tigger-zy@163.com
---
### 1. The steps of finding lane lines in a image

For  the program, the input is a 940*540 jpeg image. The output is a copy of this image which is drawed the left line and the right line of the current lane. 

![](https://github.com/flyingcow8/CarND-LaneLines-P1/blob/master/flow.jpg)

In the hough lines convert step, we draw the line on a blank canvas which has the same resolution with the original image. We do it in a function called draw_lines. The main input parameter of this function is hough lines，which consist of several lines. The target of the function is converting hough lines to two lane lines. The steps as shown blow.
1. Divide the hough lines into two parts by slope. The negative slope ones are belong to the left line part. The positive slope ones are belong to the right line part.
2. To draw the left and right lane lines, we must know the slope and the coordinates at both ends. The four points' coordinates are (left_bottom_x, left_bottom_y), (left_top_x, left_top_y), (right_bottom_x, right_bottom_y), (right_top_x, right_top_y). *left_bottom_y* and *right_bottom_y* are the height of the image. *left_top_y* and *right_top_y* are confirmed by ROI. In this case, *\*_bottom_y* is 540, *\*_top_y* is 540/2+50. So we just need to calculate all the x value.
3. Calculate the slope. Hough lines are segments of the lane lines. We use the average value of hough lines' slopes as lane lines' slopes. To avoid interference, we cut the max and min value in the two slope groups respectively before calculating the average. 
4. Calculate the two lines' bottom end x coordinate value. We extrapolate the segments(hough lines) to the bottom line(y=540) of the image. We make average of the bottom x coordinate array to get the left lane line and right lane line's buttom x value.
5. Calculate the two lines' top end x coordinate value. We have bottom end x, all y values and slopes. So it's easy to get the top end x values.
6. Now we have the two lane lines' endpoint coordinate and slope. Use cv2.line() method to draw lines. 


### 2. Potential shortcomings

- If the camera's position is changed, we have to adjust the ROI's top y coodinate value to make the result correctly.


### 3. Suggest possible improvements to your pipeline

- To make drawing lines of videos more robustness, we should improve the custom_average algorithm in draw_lines function.
- We can add kalman filter to make drawing lines of videos more robustness.
