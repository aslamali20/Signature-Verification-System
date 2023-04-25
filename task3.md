#  Plotting Histogram and Calculating Pixel Difference





## Code Explanation

	def getpix(img):
    i=0
    mx=0
    while (i < 256):
        pix = np.sum(img == i)
        if(pix>mx):
            mx=pix
        i = i + 1
        
    return mx

This Python function, getpix(img), takes an input image as a NumPy array and returns the maximum pixel value count for a single intensity value (i.e., gray level) in the image.

The function iterates through all possible intensity values (0 to 255) and uses NumPy's comparison operation to find the number of pixels in the image that have the current intensity value. It keeps track of the maximum pixel count it has seen so far and updates it if it finds a higher count.

Finally, the function returns the maximum pixel count it has found. This can be used as a measure of the image's contrast or the presence of prominent features in the image.


    test = cv2.imread('image/1.jpg',cv2.IMREAD_GRAYSCALE)
    test_img = cv2.resize(test,[150,50])

    hist1 = cv2.calcHist([test_img],[0],None,[256],[0,256])
    plt.plot(hist1)

    
    testpix1=getpix(test_img)
    testpix1


![image](https://user-images.githubusercontent.com/99079432/234320135-6caff323-8262-43f9-8161-74bafd04741f.png)








This code loads an image file named "1.jpg" from the "image" directory as grayscale using cv2.imread() and resizes it to a fixed size of 150x50 pixels using cv2.resize().

The code then uses cv2.calcHist() to compute the histogram of the grayscale image with 256 bins (one for each possible intensity value), and plots it using plt.plot().

Finally, the code calls the getpix() function with the resized image as an argument and assigns its return value to the variable testpix1. This returns the maximum count of any intensity value in the image, which can be interpreted as a measure of the image's contrast or the presence of prominent features.










      Pix_array=[]
      i=0
      arr=[]

      for filename in os.listdir(Folder):

          Diff_array=[]

          #reading images
          path=os.path.join(Folder,filename)
          img1=cv2.imread(path, cv2.IMREAD_GRAYSCALE)

          train_img = cv2.resize(img1,[150,50])
          print(filename)

          #Plotting hist
          hist = cv2.calcHist([train_img],[0],None,[256],[0,256])
          plt.plot(hist)

          pix1=getpix(train_img)

          #Calculating Difference between two images pixel values
          ans = abs(testpix1-pix1)  

          #Storing current image pixxel size in array
          Pix_array.append(pix1)

          #Storing pixel difference in array

          Diff_array.append(filename)

          Diff_array.append(ans)

          arr.append(Diff_array)

          i=i+1

![image](https://user-images.githubusercontent.com/99079432/234321339-26ea20dc-09af-4237-9a32-ce3eccbfd4f7.png)



This code appears to perform the following operations:

1.	It initializes an empty list Pix_array to store the maximum pixel counts of all images in the directory, and an empty list arr to store the pixel count differences between images.
2.	It iterates through all files in the directory specified by Folder.
3.	For each image file, it loads the image as grayscale using cv2.imread(), resizes it to a fixed size of 150x50 pixels using cv2.resize(), and computes its histogram with 256 bins using cv2.calcHist().
4.	The code then calculates the maximum pixel count of the resized image using the getpix() function and stores it in the Pix_array list.
5.	It calculates the absolute difference between the maximum pixel count of the current image and the testpix1 value computed earlier, and stores the filename and difference value as a list in the Diff_array list.
6.	The Diff_array list is appended to the arr list.
7.	The code repeats steps 3-6 for all images in the directory.
Overall, this code seems to be performing a basic image comparison based on the maximum pixel count of the images, where the difference between the maximum pixel counts of each image and a reference image (test_img) is computed and stored for further analysis.

             arr.sort(key=lambda row: (row[1]), reverse=False)

             print(arr)

This code sorts the arr list of pixel count differences in ascending order based on the second element of each list, which represents the absolute difference between the maximum pixel count of the current image and the testpix1 value computed earlier. The key=lambda row: (row[1]) argument specifies that the sorting should be done based on the second element (index 1) of each row (list), while the reverse=False argument specifies that the sorting should be in ascending order.
After the arr list is sorted, it is printed to the console using the print() function. The output will be a list of lists, where each inner list contains two elements: the filename of an image, and the absolute difference between its maximum pixel count and the testpix1 value. The list will be sorted such that the images with the smallest differences will appear first.

             sorted_list = sorted(arr, key=lambda x:x[1]) 

             sorted_list

This code does the same thing as the previous code block, but using the built-in sorted() function instead of the list.sort() method. The sorted() function takes an iterable (in this case, the arr list) and returns a new sorted list based on the specified sorting key (in this case, the second element of each inner list). The key=lambda x:x[1] argument specifies the sorting key as before, and the function returns the sorted list, which is then assigned to the sorted_list variable.

The output will be the same as the previous code block: a list of lists sorted based on the second element of each inner list, with the images with the smallest differences appearing first.

