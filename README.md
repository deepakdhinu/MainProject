# Braille to Text Translator

## Authors 
- Bárbara Côrtes e Souza (@barbaracortes)
- Lucas Fernandes Turci  (@lucasturci)

## Abstract
Given a picture containing a braille message, this apllications translates the message into text and outputs two items the original image with the ascii characters above the braille symbols.

## Project description

### Image processing techniques involved
The main image processing tasks that are going to be used are image segmentation and image enhancement to improve visualization quality allowing to recognize change of depth, texture patterns, etc.

### Application
The translator's main purpose is to contribute as an accessibility tool. With this application, one could easily translate braille to text and then be able to translate it to audio, for example. Also, it would work as a teaching device, helping children to learn braille in an easier way.

### Main objective
The main objetive for this project is to provide anyone with the ability to read any text written in braille. Therefore, it can help as a teaching device and as an accessibility tool.

To reach this goal, the idea is to enhance a picture of a braille text until every letter can be easily distinguished and identified. That is, given an image, the objetive is to apply image processing techniques on it so that every circle of a braille letter becomes well defined, let's say white, and all the other pixels become black.

With this final binary image, we want to use it to match every symbol to an english letter. This corresponding letter will be added to the image, so that the translation is visual and therefore easy to understand.

### Description of input images
Given the program's main objective, the input images that will be used are going to be any picture of a text written in braille that a person could've taken from their phone. As for the tests during the period of the development of the code, the images used are going to be retrieved manually from the internet, trying to represent the real scenario in the most reliable way possible. 

With that said, below are two examples of possible input images. 

<i><strong>Picture 1:</strong> Example image of braille text #1</i><br>
<img src="https://raw.githubusercontent.com/lucasturci/BrailleTextTranslator/master/media/images/1.png" width="540"  />

<i><strong>Picture 2:</strong> Example image of braille text #2</i><br>
<img src="https://raw.githubusercontent.com/lucasturci/BrailleTextTranslator/master/media/images/1.jpg" width="540"  />

### Description of steps

The input image will be transformed in a series of steps, one of which will make it binary using thresholding operation, so that the white pixels may correspond to the braille circle, and the black to the background (or vice versa). After that, the program will recognize the patterns of circles and output the corresponding english text. The steps are the following: 

1\. Remove noise
- The first step is to remove the noise that may complicate the steps that will follow. This can be applied after the binary transformation, using morphological erosion, or before, using image filtering.

2\. Segmentation
- The shadows of the braille circles are the components that will be used to recognize this objects. With that in mind, the program will filter the pixels that have more contrast with their neighbourhood.

3\. Thresholding
- Transform the input image in binary matrix, so that the background is black and braille circles are white (or vice versa).
- Use thresholding operation 

4\. Ignore unwanted white regions
- This step will recognize which regions don't correspond to braille circles, using comparison between circle's colour description

5\. Determine diameter D of a braille circle 
- It will be calculated as the median of the diameters of all the circles in the image

6\. Segment image into blocks
- Each block corresponds to a single letter
- The image will be segmented into a grid of cells with sizes 2·D X 3·D  

7\. For each block, determine which letter it represents 

8\. Insert corresponding letter on top of the block it represents, and output final image