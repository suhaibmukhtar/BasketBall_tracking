# Basketball Dribble Detection System

## Introduction
This repository contains code for a basketball dribble detection system using computer vision techniques. The system processes video input, detects the basketball, and analyzes dribble patterns. The goal is to extract meaningful insights such as dribble count, speed, dribbling efficiency and consistency using OpenCV in Python.
## Main Objective:
Objective: Utilize computer vision techniques to extract meaningful insights from the video of a man 
performing basketball dribble.
## Features
<ul>
  <li>Detects basketballs in video streams using color segmentation.</li>
  <li>Tracks dribbles by analyzing the movement of the basketball.</li>
  <li>Calculates dribble count and efficiency.</li>
  <li>Records dribble speeds for analysis.</li>
</ul>

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
- **Dribble Detection Criteria:** Defining the criteria for detecting a dribble based on the movement and speed of the basketball. Because the duration to complete the dribble is changing with respect to time.
## Metrics Used
  <ul>
    <li><b>Dribble Count:</b></li>
   <p>The code tracks the basketball in the video and detects dribbles based on significant changes in its position. It     
      counts the number of dribbles performed by the player during the video. Each time a significant change in position is 
      detected, indicating a dribble, the count is incremented. This metric provides insights into the player's dribbling 
      frequency and activity level during the game.</p>
   <li><b>Dribble Efficiency:</b></li>
    <p>
      Dribble efficiency measures the effectiveness of the player's dribbling technique. It is calculated by analyzing successful dribbles against total attempts. The code records the total number of dribble attempts and the number of successful dribbles detected during the video. By dividing the number of successful dribbles by the total attempts, the dribble efficiency is computed. This metric helps assess the player's skill level and proficiency in ball handling.
    </p>
  <p>
    These metrics provide valuable information about the player's dribbling performance and can be used for performance evaluation and analysis. Additionally, other metrics such as average dribble speed, direction of dribbles, and dribbling patterns can also be measured using computer vision techniques to further analyze the player's performance and playing style.
  </p>
</ul>

## Conclusion
By analyzing the video using computer vision techniques, this project aims to provide valuable insights into the basketball player's dribbling performance. The extracted metrics, such as dribble count, speed, efficiency and consistency, can be used for performance evaluation and improvement.

## Sample Output

## Code Documentation
- `bg_subtractor = cv2.createBackgroundSubtractorMOG2()`: Creates a background subtractor model.
- `mask = cv2.inRange(hsv, yellowLower, yellowUpper)`: Applies color thresholding to isolate the basketball i.e. yellow color patterns .
- `center = (int(M["m10"] / M["m00"]), int(M["m01"] / M["m00"]))`: Calculates the centroid of the basketball contour.
## Major steps documentation
## 1. Initialization and Setup
Video Path:
video_path = r"WHATSAAP ASSIGNMENT.mp4"
Specifies the path to the input video file.
HSV Color Range:
yellowLower = (20, 100, 100)
yellowUpper = (30, 255, 255)
Defines the HSV color range for detecting the yellow color of the basketball.
Deque Initialization:
pts = deque()
Initializes a deque to store tracked points.
## 2. Video Processing Loop
Video Capture:
vs = cv2.VideoCapture(video_path)
Initializes a video capture object to read frames from the video file.
Background Subtraction:
bg_subtractor = cv2.createBackgroundSubtractorMOG2()
Creates a MOG2 background subtractor to segment moving objects from the background.
Frame Processing:
Resizes the frame to a width of 500 pixels.
Applies Gaussian blur to the frame to reduce noise.
Converts the frame from BGR to HSV color space.
Applies color thresholding to isolate yellow regions (basketball) in the frame.
Contour Detection:
Finds contours in the thresholded mask to detect the basketball.
Calculates the centroid and radius of the detected basketball contour.
## 3. Dribble Detection
Dribble Thresholding:
Checks if the movement of the basketball exceeds a predefined threshold in both x and y directions to detect a dribble.
Dribble Counting:
Tracks the number of dribbles performed by the player.
Dribble Efficiency Calculation:
Calculates the dribble efficiency based on the ratio of successful dribbles to total attempts.
Dribble Speed Measurement:
Measures the speed of each dribble based on the time taken to cover a certain distance.
## 4. Display and Output
Visualization:
Draws the detected basketball and its centroid on the frame.
Displays dribble count and efficiency on the frame.
User Interaction:
Allows the user to quit the application by pressing the 'q' key.
## 5. Cleanup and Output
Release Resources:
Releases the video capture object and closes all OpenCV windows.
Print Statistics:
Prints the total dribble count, dribble efficiency, and average dribble speed (if available) to the console.
