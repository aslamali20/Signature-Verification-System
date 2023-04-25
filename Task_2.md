# Signature Detection And Extraction

####  python code extract the signature from plan sheet 

each sheet have 16 signature total 5 plane sheet for each person

total 6 person, signature total 30 plane sheet 

total 480 signature extract from 30 plane sheet

## Code Explaination

This Python code defines a function called Sign_Detect() that takes three arguments: Image, n, and Path. Image is a NumPy array that represents an image, n is an integer that is used to create filenames for the output images, and Path is a string that represents the directory where the output images will be saved.

The function first resizes the input image by a factor of 0.5 using cv2.resize(). Then, it converts the image to grayscale using cv2.cvtColor(). A binary inverse threshold is applied to the grayscale image using cv2.threshold() to create a binary image where white pixels represent regions of interest (ROI).

The function then finds contours in the binary image using cv2.findContours(). For each contour, if its area is greater than or equal to 280 pixels, a bounding rectangle is created around it using cv2.boundingRect(). A region of interest (ROI) is extracted from the original image using the bounding rectangle, and it is resized to a fixed size of 150x50 pixels using cv2.resize(). The ROI is saved to a file using cv2.imwrite() with a filename consisting of a string that includes the value of n and the contour index i.

The script then iterates over all files in a directory named image, reads each image using cv2.imread(), and calls the Sign_Detect() function on it. The integer variable i is incremented by 1 for each image, and it is used to generate unique filenames for the output images.

The purpose of this script is to detect and extract signboards from a set of input images using contour detection and bounding box extraction techniques. The extracted signboards are then saved as individual images in a new directory named image.


