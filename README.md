# EyeSeeYou

## Inspiration
In recent years, making machine learning models that can diagnose diseases has become much easier, and experienced programmers can make convolutional neural networks with decent accuracy within an hour. Because of this, any dataset you can find online has already had several machine-learning models created for it. The most difficult part of making the models nowadays is generating the data needed to make the models, which is a very time-consuming process. A more efficient process to generate data needed to be made, resulting in the vessel segmenter!

## What it does
Vessel Segmenter creates a segmentation map over IR eye scans, allowing for easier segmentation as the consumer does not have to segment every edge pixel tediously. Normally, we have to identify the vessel type, either arteries or veins, and then meticulously try and shade in every pixel for each vessel. When using our project, you just need to put the Infrared Eye PNG into the program, and it will give you a segmentation mask that can be converted to STL, and you can overlay it with the PNG file in Slicer. From there, you just need to identify the type of vessel, draw a rough outline, and then intersect the masks to create a much more accurate and speedy segmentation.

## How we built it
We spent over 6 hours of hard work making this work. We worked collaboratively on a Google Collab Notebook. We used convolutional neural networks from opencv to detect edges on the IR scans and created pixel masks to indicate edges. Image blurring and normalization techniques were used to improve its accuracy further. Then, we iterated through pixels using the positions of edges, the color of the pixel, and other data to determine for each pixel if it’s part of a vein.

## Challenges we ran into
Our big challenge was converting the PNG file from our program to an STL file to be uploaded to Slicer. We discovered that the STL file is a 3D file, and converting a 2D PNG file to a 3D STL file is difficult to code as the STL uses various 3-dimensional vectors to make the object. We attempted to make every pixel a separate vertice and add them all, but it didn’t work. We then tried to combine vertices into planes and make a 2D face, but this didn’t work as the planes had to be connected in a certain order to work. We eventually decided to find an online converter that might work. It turned out to work well enough to work correctly. The only problem after that was that the converter made the STL 3 dimensional in some places.

## Accomplishments that we're proud of
We were able to use a convolutional neural network to accurately identify the exact locations of edges across an IR image. Then, we devised a method of filling in non-edge pixels to generate an accurate segmentation mask for the IR scan. We are confident that this segmentation mask will significantly improve the efficiency of annotating such images

## What we learned
We learned a lot about different 2d and 3d file formats and the inner workings of raster and vector-based files. We also learned about how slicer(data segmentation platform) works.

## What's next for Vessel Segmenter
We will make our output file into a .stl file to appropriately be used in Slicer. Then, we plan on expanding the model's capabilities to differentiate the different arteries and veins from the image, building upon the vessel detector. Those segmentations can then be used to predict other eye diseases with much higher precision and accuracy than a model that doesn’t have artery and vein segmentation data.

## Built With
cnn, ir-scans, slicer, opencv, python

# Try it out
[ colab.research.google.com](https://colab.research.google.com/drive/1YwnCQV1WzKrrWGP-hltpWXBMl28NBVeO?usp=sharing)
