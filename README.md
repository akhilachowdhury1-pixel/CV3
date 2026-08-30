Project: Image Filtering and Blurring (Spatial Domain)
Aim
To implement and analyze the effect of various spatial filtering kernels (3x3, 5x5, 7x7, and 11x11) on grayscale images to achieve smoothing/blurring effects using both high-level libraries (OpenCV) and low-level matrix operations (NumPy).

Description
This project demonstrates how image convolution works in the spatial domain. By applying a 'Box Filter' (an averaging kernel), we replace each pixel's value with the average of its neighbors.

Kernel Sizes: Larger kernels (e.g., 7x7 or 11x11) result in a more pronounced blur because they average over a wider area, effectively removing high-frequency details (noise and sharp edges).
Implementation: The project uses cv2.filter2D for efficient computation and a nested-loop NumPy implementation to demonstrate the underlying mathematical process of convolution.
Solution Analysis & Results
Image 1 (Puppy):
<img width="877" height="812" alt="image" src="https://github.com/user-attachments/assets/9b5d8534-af1c-4463-b724-bf7a6196dccc" />

Original: Contains significant high-frequency detail and texture in the fur.
3x3 Kernel: Slight reduction in noise; the fur texture remains mostly visible.
5x5 & 7x7 Kernels: The image becomes progressively softer. Features like the eyes and nose start to lose sharpness.
Image 2 (Couple with Umbrella):
<img width="950" height="779" alt="image" src="https://github.com/user-attachments/assets/0f3801d2-79e4-4383-aedb-5248593da217" />

Original: A complex scene with trees (fine detail) and distinct edges between the subjects and the background.
Manual 11x11 NumPy Filter: This larger kernel creates a significant 'heavy' blur. The fine leaves in the background merge into a soft texture, and the outlines of the figures become highly diffused.
Conclusion
As the kernel size increases, the intensity of the blur increases, illustrating the low-pass filtering property where sharp transitions are smoothed out.

