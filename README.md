
Aim:
 
To write a python program using OpenCV to capture the image from the web camera and do the following image manipulations.
i) Write the frame as JPG 
ii) Display the video 
iii) Display the video by resizing the window
iv) Rotate and display the video

## Software Used
Anaconda - Python 3.7
## Algorithm

1.Import CV2,numpy and the other required libraries


2.Create an instance of Video Capture and save the displayed image


3.Capture video and using numpy resize the shape of the window and display the video

4.Rotate the captured image by 180*

## Program:
``` Python
### Developed By: Karthikeyan R
### Register No: 212222240045

## i) Write the frame as JPG file

import cv2
obj = cv2.VideoCapture(0)
while True:
    cap,frame = obj.read()
    if not cap:
        break
    cv2.imshow('video',frame)
    cv2.imwrite('picture.jpg',frame)
    if cv2.waitKey(1) == ord('q'):
        break
obj.release()
cv2.destroyAllWindows()

## ii) Display the video

img = cv2.VideoCapture(0)
while True:
    image,frame = img.read()
    cv2.imshow('pic',frame) 
    if cv2.waitKey(1)==ord('q'):
        break
img.release()
cv2.destroyAllWindows()

## iii) Display the video by resizing the window

import numpy as np
capture = cv2.VideoCapture(0)
while True:
    ret,frame=capture.read()
    if not ret:
        break
    height,width = frame.shape[:2]
    smaller_frame=cv2.resize(frame,(width//2,height//2))
    image = np.zeros((height,width,3),dtype=np.uint8)
    image[:height//2,:width//2]=smaller_frame
    image[height//2:, :width//2]=smaller_frame
    image[:height//2, width//2:]=smaller_frame
    image[height//2:, width//2:]=smaller_frame

    cv2.imshow('PIC',smaller_frame)
    
    if cv2.waitKey(1)==ord('q'):
        break
capture.release()
cv2.destroyAllWindows()

## iv) Rotate and display the video

capture = cv2.VideoCapture(0)
while True:
    ret,frame=capture.read()
    if not ret:
        break
    height,width = frame.shape[:2]
    smaller_frame = cv2.resize(frame,(width//2,height//2))
    image = np.zeros((height,width,3),dtype=np.uint8)

    image[:height//2,:width//2]=cv2.rotate(smaller_frame,cv2.ROTATE_180)
    image[height//2:, :width//2]=smaller_frame
    image[:height//2, width//2:]=smaller_frame
    image[height//2:, width//2:]=cv2.rotate(smaller_frame,cv2.ROTATE_180)
    
    cv2.imshow('ROTATE_PIC',image)
    if cv2.waitKey(1) == ord('q'):
        break
capture.release()
cv2.destroyAllWindows()

```
## Output

### i) Write the frame as JPG image

![image](https://github.com/user-attachments/assets/04f4b1d5-fc0a-443f-854e-0c0c2027a4e8)


### ii) Display the video

![image](https://github.com/user-attachments/assets/c593f3f9-8b93-4cb9-93db-c7530fcd48e1)


### iii) Display the video by resizing the window

![image](https://github.com/user-attachments/assets/96363df0-0229-4c01-89bf-a0879bd10156)


### iv) Rotate and display the video

![image](https://github.com/user-attachments/assets/0d849b87-ee1e-4dc5-93bb-73b840712bd5)


## Result:
Thus the image is accessed from webcamera and displayed using openCV.
