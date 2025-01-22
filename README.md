# Image Classifier

## A scaled down version of an image classifier that uses Convolutional Neural Networks to classify any images any number of classes. 
---
## Overview
 
This project is to serve as an introduction to CNNS and thier capabilities. The main classifer is a binary classifer which can classify two classes at a time. To classify more than two classes you will need to just uncomment a few lines in the jupyter notebook. As for the dataset, I have downloaded images using an extension called [Download All Images
](https://download-all-images.mobilefirst.me).

---

## Conuvoluational Neural Network 
A Convolutional Neural Network (CNN) is a type of deep learning architecture specifically designed for processing data with a grid-like topology, such as images. It leverages the concept of convolution, a mathematical operation that involves sliding a filter (or kernel) over the input data to extract local features. Key characteristics of a CNN include:

 * Convolutional Layers: These layers are the core of CNNs. They use small filters (kernels) to scan the input image, extracting local features such as edges, corners, and textures. This approach allows CNNs to capture spatial relationships between pixels, which is crucial for understanding visual information.   
* Pooling Layers: These layers downsample the feature maps generated by convolutional layers, reducing their spatial dimensions while preserving the most important information. This helps to:   
  - Reduce computational cost: By decreasing the number of parameters, pooling layers make the network more efficient.   
  - Improve invariance to small translations and distortions: Pooling makes the network less sensitive to slight shifts or rotations of objects in the image.   

* Parameter Sharing: CNNs share weights (parameters) across different locations in the input image. This means that the same filter is applied repeatedly to different parts of the image, significantly reducing the number of parameters and improving generalization.   

* Hierarchical Feature Learning: CNNs learn a hierarchy of features, starting with simple low-level features (edges) and gradually building up to more complex high-level features (objects).This hierarchical representation allows CNNs to capture intricate patterns and relationships within images.   

---
## Code Structure

### 1. **Libraries**
- **OpenCV**: Captures video input.
- **Tensorflow**: Trains the neural Network.
- **MatplotLib**: Plots all graphs.
- **Imghdr**: Controls the image selection.
- **Numpy**: Performs complex calculations.
- **Os**: Handles files and directories.

### 2. **Data Preprocessing**
This is done using : 
- Filtering by file types.It checks if the image files belong to a specific set of allowed extensions (defined in `image_exts`).If an image file has an unsupported extension,it is identified and removed. 
- Handling potential issues:A try-except block to catch any exceptions that might occur during image reading (e.g., corrupted files, invalid file formats).If an issue is encountered, it logs the problematic image path and optionally removes the file.

### 3. **Neural Network Architecture**
-  Input Layer `input_shape=(256, 256, 3)`: This specifies that the input to the network is a 3-dimensional tensor representing an image with a height and width of 256 pixels and 3 color channels (Red, Green, Blue).
. Convolutional Layers:

- Convoloutional Layers `Conv2D(16, (3,3), 1, activation='relu')`:This is the first convolutional layer.
16: The number of filters (kernels) used in this layer. Each filter learns to detect specific features in the input image.
(3,3): The size of the convolutional filters, which are 3x3 pixels. 1: The stride of the convolution, meaning the filter moves 1 pixel at a time.ctivation='relu': The Rectified Linear Unit (ReLU) activation function is applied to introduce non-linearity into the network.
  - MaxPooling2D( )`Conv2D(32, (3,3), 1, activation='relu')`: The second convolutional layer with 32 filters.This layer performs max pooling, which downsamples the feature maps by selecting the maximum value within a 2x2 window. This helps to reduce the spatial dimensions of the feature maps and extract the most important features.

  - MaxPooling2D( ) `Conv2D(16, (3,3), 1, activation='relu')`:The third convolutional layer with 16 filters which further downsamples the feature maps.

  - MaxPooling2D( ): The final max pooling layer.

- Flatten Layer`Flatten()`: This layer converts the 3D feature maps from the previous convolutional layer into a 1D vector. This is necessary to feed the output of the convolutional layers into the subsequent fully connected layers.

- Fully Connected Layers`Dense(256, activation='relu')`: The first fully connected (dense) layer with 256 neurons.ReLU activation is applied here as well.
- Output Layer`Dense(1, activation='sigmoid')`: The output layer with a single neuron.The sigmoid activation function is used to produce a probability between 0 and 1, which can be interpreted as the likelihood of the input image belonging to a particular class (binary classification).

Model Summary : 

![image](https://github.com/user-attachments/assets/d02e6ef8-0d2f-4059-9c31-3ad53001f300)

---

## Usage Instructions 

### 1.**Setup**
- Search for any images in your browser and click on the
- It will automatically download all images in a zip file and save it on your system. In this case I downloaded pictures of cats and dogs and uploaded them onto the colab workspace.
- Give relevant paths to the image files.

### 2.**Testing**
- Select any image from your test images folder.
- Edit the paths in the in the code blocks and simply run the cell.
  
### 3.**Evaluate**
- Evalauate the model using performance plots. Make changes accordingly.


--- 

## Prerequisites
Ensure the following libraries and dependencies are installed:
- Python 3.7 or higher
- Required Python libraries:
  ```bash
  pip install opencv-python numpy tensorflow standard-imghdr mayplotlib
  ```
---
## License
This project is licensed under the MIT License. You are free to use, modify, and distribute the code.

---
Feel free to reach out with suggestions or improvements! 
<br>
Reference Video : (https://youtu.be/jztwpsIzEGc?si=_ziK1wDiBoPd5qpS)


