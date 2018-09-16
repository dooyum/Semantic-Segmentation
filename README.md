# Semantic Segmentation
### Introduction
In this project, I labeled the pixels of a road in images using a Fully Convolutional Network (FCN).

### Setup
##### FCN Model
This project was built upon the [VGG-16 Fully Convolutional Network for Semantic Segmentation](https://arxiv.org/pdf/1411.4038.pdf). I created an FCN that took the output of VGG-16 as it's input and trained it to segment a road from its surroundings. The model was trained using the [Kitti Road dataset](http://www.cvlibs.net/datasets/kitti/eval_road.php) in which roads have been labeled to tell them apart from the surroundings. You can download the dataset from [here](http://www.cvlibs.net/download.php?file=data_road.zip).


### Building the FCN
I built the new FCN by performing a 1x1 convolution on the output (7th layer) of a VGG-16. After which I upscalled the output of my FCNs first layer by quadrupling the kernel size and doubling the stride. After this, I created a new layer in my network by performing a 1x1 convolution from 4th layer of the VGG-16 Network and applying a skip layer from that same layer to my 2nd layer. After this, I upscaled the ouput of my 2nd layer and performed a third 1x1 convolution on the 3rd layer of the VGG-16 network. I fed this new convolution with a skip layer from the VGG-16 3rd layer into the final layer of my FCN. The final Layer performs one last upscaling to a Tensor which reflects the desired dimensions of the image being classified as well as the number of classes we have, which in our case is two (Road/Not a road).

### Results
On one of my early test runs, the new classifier did a decent job figuring out where the road was, even though I trained it with just 6 epochs and a batch size of 5.

# Semantic Segmentation
### Introduction
In this project, I labeled the pixels of a road in images using a Fully Convolutional Network (FCN).

### Setup
##### FCN Model
This project was built upon the [VGG-16 Fully Convolutional Network for Semantic Segmentation](https://arxiv.org/pdf/1411.4038.pdf). I created an FCN that took the output of VGG-16 as it's input and trained it to segment a road from its surroundings. The model was trained using the [Kitti Road dataset](http://www.cvlibs.net/datasets/kitti/eval_road.php) in which roads have been labeled to tell them apart from the surroundings. You can download the dataset from [here](http://www.cvlibs.net/download.php?file=data_road.zip).


### Building the FCN
I built the new FCN by performing a 1x1 convolution on the output (7th layer) of a VGG-16. After which I upscalled the output of my FCNs first layer by quadrupling the kernel size and doubling the stride. After this, I created a new layer in my network by performing a 1x1 convolution from 4th layer of the VGG-16 Network and applying a skip layer from that same layer to my 2nd layer. After this, I upscaled the ouput of my 2nd layer and performed a third 1x1 convolution on the 3rd layer of the VGG-16 network. I fed this new convolution with a skip layer from the VGG-16 3rd layer into the final layer of my FCN. The final Layer performs one last upscaling to a Tensor which reflects the desired dimensions of the image being classified as well as the number of classes we have, which in our case is two (Road/Not a road).

### Results
On one of my early test runs, the new classifier did a decent job figuring out where the road was, even though I trained it with just 6 epochs and a batch size of 5.

[](./old_runs/image1.png)
[](./old_runs/image2.png)
[](./old_runs/image3.png)
[](./old_runs/image4.png)
[](./old_runs/image5.png)
[](./old_runs/image6.png)
[](./old_runs/image7.png)

#### Final Result
I tuned my training variables to run for 120 epochs with a batch size of 10 and a 25% dropout rate. I was pretty happy with the results
[](./runs/image.png)
