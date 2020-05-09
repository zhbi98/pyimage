# **Image processing**  
![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg) 

**Here mainly realizes the common image processing such as fisheye correction, Gaussian blur, transparency, saturation sharpening, gray filling, arbitrary angle rotation and so on. These algorithms are implemented from the bottom through Python, and the implementation process of each algorithm is described in detail below**

# _I. Alpha_
The image is made up of a series of pixels, and the original colors of the image are displayed by the pixels emitting light.The color of each pixel of the image is composed of standard colors R, G and B.So when the image is processed by the algorithm, the RGB value of the pixel of the image is actually re-calculated A process of recombination of calculations.

For processing the transparency of the image through the algorithm, it is actually on the original image through the algorithm Cover with a layer of colored mask. The color of the mask can be any combination of RGB.That is to say, for an image A, it is covered with a mask B, what we can seeThe image C is the image A seen through the mask B.So what we actually see is the RGB value of image C.

So what we have to do is to calculate the RGB value of image C.

#### 1.So transparency blending algorithm:
`A(C) = (1-alpha)*A(B) + alpha*A(A)` 

`R(C) = (1-alpha)*R(B) + alpha*R(A)`  
`G(C) = (1-alpha)*G(B) + alpha*G(A)`  
`B(C) = (1-alpha)*B(B) + alpha*B(A)`

#### 2.Algorithm effect:  
![image]("https://github.com/zhbi98/image/blob/master/Sierra17.jpg")
