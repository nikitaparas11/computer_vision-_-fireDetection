# computer_vision-_-fireDetection
This Python script is designed to detect fire-like colors in a video feed captured from a webcam using computer vision techniques. It uses the OpenCV library for video capture, image processing, and object detection, and NumPy for numerical operations. The primary goal of this system is to identify areas within the frame that exhibit fire-like colors, highlight them with bounding boxes, and display a message indicating that fire has been detected.


1. Imports and Setup
cv2 (OpenCV) and numpy are imported to handle image processing tasks.
cv2.VideoCapture(0) initializes the webcam feed (the 0 parameter refers to the default camera).
2. Fire Detection Function (detect_fire)
This function processes each frame from the video feed and identifies potential fire areas based on color:

Color Conversion: Each frame from the video is converted from the BGR color space (default in OpenCV) to HSV (Hue, Saturation, Value) color space. HSV is chosen because it is more robust for color detection under varying lighting conditions.
Thresholding: A mask is created to isolate pixels that fall within a specific range of HSV values, corresponding to the colors typically found in fire (such as red and orange). The range is defined as lower_bound = [0, 110, 100] and upper_bound = [35, 255, 255] to capture fire-like hues.
Morphological Operations: A closing operation (cv2.MORPH_CLOSE) is applied using a rectangular kernel to remove small noise in the mask and fill gaps in the detected fire areas.
Contour Detection: The cv2.findContours function identifies continuous regions in the mask that correspond to potential fire areas. For each contour, a bounding box is drawn around it if its area exceeds a set threshold (500 pixels), helping to ignore small irrelevant regions.
Bounding Boxes and Text: The function then overlays a red rectangle around the detected fire area and adds the text "Fire detected!" above the bounding box.
3. Video Capture Loop
The video feed is continuously read from the webcam using video.read().
Each frame is passed to the detect_fire() function for processing.
The processed frame (with bounding boxes and text) is displayed in a window titled "Fire Detection" using cv2.imshow().
The loop runs until the user presses the 'q' key to exit.
4. Resource Cleanup
When the loop ends (user presses 'q'), the video capture is released using video.release(), and all OpenCV windows are destroyed with cv2.destroyAllWindows().
5. Real-time Detection and Display
The system runs in real-time, continuously processing and displaying the video frames.
If fire-like areas are detected, they are highlighted with bounding boxes and labeled accordingly.
Conclusion
The script provides a simple, yet effective way to detect fire-like colors in a live video feed, using computer vision techniques such as color thresholding, contour detection, and morphological transformations. While the system works for general fire detection in terms of color, it may have limitations in handling complex or non-standard fire appearances (e.g., different fire colors or sizes).



