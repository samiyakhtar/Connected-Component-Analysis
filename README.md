#### The goal of this assignment is to use Stacks and Queues to perform floodfill operation and to understand the behavior of the two data structures. ####

The goal of this assignment is to perform a common image processing operation known as connected component analysis.
This operation has many uses, among which, one is to count the number of objects of interest present in an image.  The operation
assumes that the objects have been segmented using a segmentation operation, such as thresholding.  Hence, the image assumes all
objects of interest have been assigned a pixel value of 255 while all other pixels have a value of 0.  Connected component analysis
finds all objects in the image, where an object is considered a collection of pixels that are spatially connected.  Hence, all pixels having
a value of 255 and that are adjacent to each other withing a 2 dimensional grid would be considered an object.  Having identified each object,
connected component analysis results in each object being assigned a unique color to distinguish it from other objects in the image.

In performing the connected component analysis operation, one solution is to implement flood-fill algorithm. 
Flood fill algorithm is typically used for (re)coloring the adjacent areas in an image. 
Starting from a pixel at the position (x,y), this algorithm explores the image pixel by pixel, by visiting the 
neighboring pixels of any pixel it has previously visited. Each visited pixel, if its color matches the target color, 
gets repainted in the replacement color. If the pixel color does not match the target color, the algorithm stops. 
This way, it visits and repaints all the adjacent pixels of the target color. It stops when it reaches the outer 
borders of the target area. The neighboring pixels of any pixel are the eight connected pixels as shown below, 
and labeled 1 to 8, with the pixel under consideration labeled as P:

1 2 3<br>
4 P 5<br>
6 7 8<br>

In this assignment, we want to use Stacks and Queues to perform flood-fill. You are to implement the flood-fill algorithm that takes three parameters: a row position, column position, and a replacement color. 
The existing color at the provided (row,column) position in the image is the target color.

For example, consider the 32x32 image showing several stars and planets.  This image can be thresholded using the method of 
class **MyImage** from Assignment 1, resulting in an image showing several groups of pixels in white with a black background. 
The segmented structures (starts and planets) have intensity (255,255,255) while the background has intensity (0,0,0). 
represented as trichromatic values compatible with the PPM image format we worked with in the previous assignment. 
Connected component analysis is performed by scanning the image left to right, top to bottom.  If it encounters a 
pixel with value 255, it will execute the flood-fill algorithm.

As an example, assume that the first pixel with value 255 is encountered at location (10,10) as the row, column. In this case,
the target value for the flood-fill algorithm is 255 and the replacement intensity value would be given by a unique trichromat value to represent
the image object number.  If that unique trichromat value is chosen to be (255,0,0), the resulting image would replace all the pixels having the value of 255 
surrounding (10,10) with (255,0,0), thereby showing the image object as having color red.  The connected component analysis 
would continue scanning remainder of the image to find the next pixel with value 255 that has not already been considered by the flood-fill algorithm.

In this assignment, you are given the implementation of the Stack and the Queue class in the files **dpcourse/Stack.py** 
and **dpcourse/Queue.py**, respectively. Along with that, the implementation of the MyImage class along with its methods 
is also provided in **imageops/DSImage.py**.  The connected component analysis is implemented as part of a new class named
**RegionAnalysis**, a shell implementation of which is provided in the file **imageops/RegionAnalysis.py**.  This class 
is designed to manage a binary image and to perform connected component analysis resulting in a label image.  The label image
is a color image where each image object in the binary image has been identified and assigned a unique color value (a trichromatic pixel value).
In addition, a count of the number of objects is also maintained.  Several methods are already implemented in this class.  
Please write two additional methods in this RegionAnalysis class, connected_components_stack and connected_components_queue, 
that uses Stacks and Queues, respectively, to implement the operation. You will also need to implement a way to ensure that a unique trichromatic value
is used for each image object.

You are also given the driver program (ca-02.py) that calls methods to perform connected component analysis. 
Once you finish writing your methods, the driver program will also report time required in performing connected
component analysis using Stack as well as Queue.  You are to consider the benefits or limitations of using these
two data structure to perform connected component analysis, and report on your findings in the file **REPORT.md**.

**Note:**

**Do not use any in-built functions or external modules/libraries for image operations (E.g: np.mean, PIL).** In general, you can use function from math and random library. <br/>
   
  - Please do not change the code structure.
  - Usage:
   
        - python ca-02.py -i <image-name> -t <threshold-value> -d 0
        - Example: python ca-02.py -i Images/hubble.ppm -t 120 -d 0
  - Please make sure the code runs when you run the above command from prompt/terminal
  - All the output images and files are saved to "output/" folder
  - You can set the value of -d to 1 if you would like to display images so you can verify them
  - In this case, the example usage would be:
  
        - Example: python ca-02.py -i Images/hubble.ppm -t 120 -d 1

Several images are provided for testing in the folder Images: e.g., Images\hubble.ppm and Images\hubble.pgm.<br>

**PS. Please do not change: ca-02.py, dpcourse/Stack.py, dpcourse/Queue.py, imagesops/DSImage.py, requirements.txt, and Jenkinsfile.**

-----------------------

<sub><sup>
License: Property of Quantitative Imaging Laboratory (QIL), Department of Computer Science, University of Houston. This software is property of the QIL, and should not be distributed, reproduced, or shared online, without the permission of the author This software is intended to be used by students of the Data Programming course offered at University of Houston. The contents are not to be reproduced and shared with anyone with out the permission of the author. The contents are not to be posted on any online public hosting websites without the permission of the author. The software is cloned and is available to the students for the duration of the course. At the end of the semester, the Github organization is reset and hence all the existing repositories are reset/deleted, to accommodate the next batch of students.
</sub></sup>
