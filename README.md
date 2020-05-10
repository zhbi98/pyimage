# **Image processing**  
![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg) 

**Here mainly realizes the common image processing such as fisheye correction, Gaussian blur, transparency, saturation sharpening, gray filling, arbitrary angle rotation and so on. These algorithms are implemented from the bottom through Python, and the implementation process of each algorithm is described in detail below**

## _Ⅰ. Alpha_
The image is made up of a series of pixels, and the original colors of the image are displayed by the pixels emitting light.The color of each pixel of the image is composed of standard colors R, G and B.So when the image is processed by the algorithm, the RGB value of the pixel of the image is actually recalculated A process of recombination of calculations.

For processing the transparency of the image through the algorithm, it is actually on the original image through the algorithm Cover with a layer of colored mask. The color of the mask can be any combination of RGB.That is to say, for an image A, it is covered with a mask B, what we can seeThe image C is the image A seen through the mask B.So what we actually see is the RGB value of image C.

So what we have to do is to calculate the RGB value of image C.

#### 1.So transparency blending algorithm:
`A(C) = (1-alpha)*A(B) + alpha*A(A)` 

`R(C) = (1-alpha)*R(B) + alpha*R(A)`  
`G(C) = (1-alpha)*G(B) + alpha*G(A)`  
`B(C) = (1-alpha)*B(B) + alpha*B(A)`

#### 2.Algorithm effect:  
_original image1_  
<img src="https://s1.ax1x.com/2020/05/10/Y3PShR.jpg" alt="GitHub" title="GitHub,Social Coding" width="600" height="338" />  
_original image2_  
<img src="https://s1.ax1x.com/2020/05/10/Y3mHIK.jpg" alt="GitHub" title="GitHub,Social Coding" width="600" height="338" />  
_original image1 monochrome mixing_  
<img src="https://s1.ax1x.com/2020/05/10/Y3n7Os.jpg" alt="GitHub" title="GitHub,Social Coding" width="600" height="338" />  
_original image1 and image2 mixing_  
<img src="https://s1.ax1x.com/2020/05/10/Y3ui01.jpg" alt="GitHub" title="GitHub,Social Coding" width="600" height="338" />  
:+1:The effect looks good!

## _Ⅱ. binarizations_
Image binarization, as the name implies, is to convert the RGB color values of the image to 0 or 1, that is, an image is only composed of 0 and 1, in the field of electronic technology, 0 represents closed 1 represents open, for pixels 0 represents no display 1 stands for display, so the image after a binarization operation consists of only black and white. This is widely used in machine vision, because for computers, they can only process 0-1 data, and do not need to know what color the image is. They only need to know the outline of the image, so they know 0 and 1 are enough.

Before performing the binarization operation, we have to perform another operation, that is, to convert the image to a grayscale image. Why is such an operation required?
Here I will talk about the dimension of the image. For a photo, it is composed of a series of pixels, so when we want to control a certain pixel, we can communicate index through rows and columns, such as [x, y], but just x and y are not enough, why? Because x and y only describe where this pixel is Ah, it does not describe what color this pixel is. So we also need to introduce a z, use z to specify the color value, and use the color value to describe what the pixel is. colored. so there is [x, y, z], indicating that the position of this pixel is [x, y] and the color is z. so describing a pixel that constitutes a color photo needs to three-dimensional data to represent.so for a color picture it is a three-dimensional data matrix.therefore, the picture is processed into gray, which can reduce the color dimension of the image.

#### Gray filling algorithm:  
`gray = 0.299 * r + 0.587 * g + 0.114 * b`  
>This is a psychological formula, but it can also be used to process the image into gray, which is interesting, r, g, b Indicates how many standard red, green, and blue pixels each make up of the original image pixels.  

_original image_  
<img src="https://s1.ax1x.com/2020/05/10/Y3PShR.jpg" alt="GitHub" title="GitHub,Social Coding" width="600" height="338" />   
_Look, this is how it looks_  
<img src="https://s1.ax1x.com/2020/05/10/Y3YKGn.jpg" alt="GitHub" title="GitHub,Social Coding" width="600" height="338" />  
After the image is processed into gray, there is no color, which means R = G = B = gray, so the color dimension of the color photo is also reduced, so this is also similar to a proportional mixing, mixing RGB values of color photos in a ratio of 0.299: 0.587: 0.114
