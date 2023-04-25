# SCAN IMAGES

python code to scan each signature and store in folder all will worked as automatically 

## Prerequisites
1. Python >=3.6
2. OpenCV
3. Scipy 
4. Scikit-image

## Code Explanation

•	 cv2 is the OpenCV library for computer vision.

•	 imutils is a package of convenience functions to make basic image processing tasks easier.

•	 threshold_local is a function from the skimage.filters module that performs local thresholding of an image.

•	 numpy is the NumPy library for numerical computing in Python.

•	 glob is a module that provides a way to retrieve files/pathnames matching a specified pattern.

•	 os is a module that provides a way to interact with the operating system, such as getting information about the file system or changing the current working directory.

• Then, it sets a path variable to a specified directory location using the glob module to iterate over all files in the directory that match a given pattern. For each file, the script reads the image using cv2.imread() and resizes it using imutils.resize() so that its height is 2000 pixels.

• The image is then converted to grayscale using cv2.cvtColor() and local thresholding is applied to it using skimage.filters.threshold_local() function. The thresholded image is then saved to the aalam_scan directory using cv2.imwrite(), with the filename consisting of an index number bb and the .png extension.

• Finally, the script closes all windows opened by OpenCV using cv2.destroyAllWindows().

• The purpose of this script is to process a set of images located in a specified directory, applying local thresholding to them, and saving the thresholded images to a new directory.




