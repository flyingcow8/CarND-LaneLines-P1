# **Finding Lane Lines on the Road** 
##ZHAN YUAN,  tigger-zy@163.com
---
### 1. The steps of finding lane lines in a image

For  the program, the input is a 940*540 jpeg image. The output is a copy of this image which is drawed the left line and the right line of the current lane. 

```flow
st=>start
read=>operation: Read the original RGB image
gray=>operation: Grayscale convert
gaussian=>operation: Gaussian smoothing handling
canny=>operation: Canny edge convert
roi=>operation: Get the region of current lane
hough=>operation: Hough lines convert
combine=>operation: Combine lane lines with original image
save=>operation: Save the result as a new file
e=>end
st->read->gray->gaussian->canny->roi->hough->combine->save->e
```




### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
