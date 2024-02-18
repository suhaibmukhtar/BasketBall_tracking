# Basketball Dribble Analysis using Computer Vision

## Introduction
This project utilizes computer vision techniques to analyze a video of a basketball player performing dribbling drills. The goal is to extract meaningful insights such as dribble count, speed, and consistency using OpenCV in Python.

## Analysis Methods
- **Background Subtraction:** The video frames are processed using a background subtractor (MOG2) to extract the foreground, i.e., the basketball and the player, from the background.
- **Object Detection:** Color thresholding in the HSV color space is applied to detect the basketball. Contours are then used to track its movement.
- **Motion Tracking:** The motion of the basketball is tracked to identify dribbling patterns. A sustained movement in a certain direction and speed is considered a dribble.

## Algorithms Used
- **BackgroundSubtractorMOG2:** This algorithm models the background of the video and identifies moving objects.
- **cv2.inRange:** Used for color thresholding to isolate the basketball based on its yellow color.
- **Contour Detection:** Used to find the contour of the basketball for tracking its movement.

## Challenges Faced
- **Parameter Tuning:** Adjusting parameters for background subtraction, color thresholding, and contour detection to improve accuracy and reduce noise.
- **Noise Reduction:** Implementing techniques to reduce noise in the video, such as eroding and dilating the mask.
- **Dribble Detection Criteria:** Defining the criteria for detecting a dribble based on the movement and speed of the basketball.

## Code Documentation
- `bg_subtractor = cv2.createBackgroundSubtractorMOG2()`: Creates a background subtractor model.
- `mask = cv2.inRange(hsv, yellowLower, yellowUpper)`: Applies color thresholding to isolate the basketball.
- `center = (int(M["m10"] / M["m00"]), int(M["m01"] / M["m00"]))`: Calculates the centroid of the basketball contour.

## Conclusion
By analyzing the video using computer vision techniques, this project aims to provide valuable insights into the basketball player's dribbling performance. The extracted metrics, such as dribble count, speed, and consistency, can be used for performance evaluation and improvement.

## Sample Output
![output](https://github.com/Sarthaksaraf96/Startup-In-Stealth-Mode-Assignment/assets/132260196/887de7c4-215f-44a1-ba6c-fdab6b87d13d)

