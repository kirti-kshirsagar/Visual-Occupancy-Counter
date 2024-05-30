# Visual Occupancy Counter

## Task: 
People Counter using YOLOv8

## My video input file:
[Input Video](https://drive.google.com/file/d/1MR3zPqQX2qtoIYyjxgUyE8qr8dLElc-D/view?usp=sharing)

## Instruction to run the code:
- Ensure **Python** is installed in your system, or else you can even use Google Colab. I used **Google Colab** with **T4 GPU**.
- Download the **YOLOv8 model** file *yolov8n.pt* and place it in the same directory as the script.
- Place the *video file* you want to process and count the people from in the same directory as the script and rename it to **user_activities.mp4**.
- Run the script using the following command in your terminal
    - python people_counter.py
- Upon running the script, a JSON file named **activities.json** will contain the output.

## Dependencies:
This script depends on the following Python packages and hence need to be installed:
- OpenCV
- Ultralytics

These can be installed using
- pip install opencv-python
- pip install ultralytics

## Approach:
1. Importing Libraries: The script imports necessary libraries including **cv2** for video processing, **json** for JSON file manipulation, and **YOLO from Ultralytics** for object detection using the YOLOv8 model.

2. Main Function: The process_video function is the main function of the script. It takes the input video file path and the output JSON file path as arguments.

3. Loading YOLOv8 Model: The YOLOv8 model is loaded using the YOLO class from Ultralytics.

4. Opening Video File: The video file is opened using cv2.VideoCapture. If the file fails to open, an error message is printed and the function exits.

5. Processing Frames: The script loops over each frame in the video. For each frame:
    - The frame is read and converted to RGB format.
    - YOLOv8 is used to predict objects in the frame, and the bounding boxes of detected objects are extracted.
    - The number of people (class 0) detected in the frame is counted.
    - The current timestamp of the frame is calculated based on the frame index and the video's frames per second (fps).
    - If there is a change in the number of people compared to the previous frame, a count change event (ENTER or EXIT) is recorded along with the timestamp.
    - The total people count at the current second is logged.

6. Output Preparation: After processing all frames, the count change events and total people count data are organized into a dictionary.

7. Writing to JSON File: The output dictionary is written to a JSON file specified by the output_file path.

