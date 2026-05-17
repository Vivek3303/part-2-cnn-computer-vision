# part-2-cnn-computer-vision
---
Data Source: https://drive.google.com/drive/folders/1akV6po4Nrgkc3yQrJkzA6cJlV-wBvUYs?usp=sharing
---
## Task 1: Problem Identification
The dataset represents an **Image Classification** problem. We are given whole images of products and tasked with categorizing the entire image into one of four mutually exclusive classes (`normal`, `scratch`, `dent`, `stain`). We are not tasked with plotting bounding boxes around the defects (Object Detection) or outlining their exact pixels (Segmentation).

## Task 5: Model Performance
After implementing a randomized train/validation split to ensure all defect types were represented, the custom CNN achieved an overall validation accuracy of **94%**. 
* The model perfectly identified `stain` defects (100% Precision, 100% Recall).
* The model achieved excellent recall (94%) on `scratch` defects and 91% on `dent` defects.
* Training and validation loss tracked smoothly and consistently together over 15 epochs, demonstrating that the network's spatial pooling and dropout layers successfully prevented overfitting.

## Task 6: CNN Concept Explanation
* **What is Convolution?**
Convolution is the process of extracting features from an image. You can think of it like shining a small "torchlight" (a filter or kernel) over the top-left corner of an image and sliding it across the entire picture. As it slides, it performs a simple dot product math operation to detect low-level features like edges, curves, and specific colors.
* **Why is pooling used?**
Pooling (specifically Max Pooling) is a sub-sampling technique used to shrink the spatial dimensions of the image representation. It takes a small matrix (like 2x2 pixels) and keeps only the maximum value. This drastically reduces computational load while ensuring that the most important extracted features are preserved, even if the image is slightly shifted.
* **Why is ReLU commonly used in CNNs?**
ReLU (Rectified Linear Unit) is an activation function that introduces non-linearity. It mathematically ignores negative pixel values (turning them to 0) while keeping positive values as they are. This helps the network solve the "vanishing gradient" problem and effectively highlights the important visual features extracted during convolution.
* **Why are CNNs better than regular feed-forward networks for image data?**
If we flattened a standard image for a regular dense network, it would result in millions of independent input nodes. A standard network treats every single pixel independently, completely losing the "spatial relationship" between pixels. CNNs share parameters (filters) across the image, meaning they understand that pixels next to each other form cohesive shapes, lines, and textures.

## Task 7: Business Use Case Mapping
**Domain: Manufacturing & Quality Control**
In a modern manufacturing plant, items on a conveyor belt are often moving too quickly for the human eye to consistently inspect without fatigue. This CNN classification model can be deployed at the edge (directly on an IoT camera over the assembly line). 
As products pass, the camera captures an image, and the CNN predicts if the item is `normal` or defective (`scratch`, `dent`, `stain`) in milliseconds. If a defect is classified, the system can trigger an automated robotic arm to divert the defective product off the line, ensuring that only high-quality items reach the packaging phase, saving both time and human labor costs.
