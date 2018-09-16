[//]: # (Image References)
[image1]: ./old_runs/image1.png
[image2]: ./old_runs/image2.png
[image3]: ./old_runs/image3.png
[image4]: ./old_runs/image4.png
[image5]: ./old_runs/image5.png
[image6]: ./old_runs/image6.png
[image7]: ./old_runs/image7.png

[image8]: ./new_runs/image1.png
[image9]: ./new_runs/image2.png
[image10]: ./new_runs/image3.png
[image11]: ./new_runs/image4.png
[image12]: ./new_runs/image5.png
[image13]: ./new_runs/image6.png
[image14]: ./new_runs/image7.png
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

![alt text][image1]
![alt text][image2]
![alt text][image3]
![alt text][image4]
![alt text][image5]
![alt text][image6]
![alt text][image7]

#### Final Result
We tuned the training variables to run for 120 epochs with a batch size of 10 and a 25% dropout rate. We recieved much better results.

![alt text][image8]
![alt text][image9]
![alt text][image10]
![alt text][image11]
![alt text][image12]
![alt text][image13]
![alt text][image14]

```
Training...Epoch: 0
Epoch loss:  41.4515908241
Training...Epoch: 1
Epoch loss:  1.91133619547
Training...Epoch: 2
Epoch loss:  1.79958974123
Training...Epoch: 3
Epoch loss:  1.73822455406
Training...Epoch: 4
Epoch loss:  1.68158416152
Training...Epoch: 5
Epoch loss:  1.61621398926
Training...Epoch: 6
Epoch loss:  1.54443276525
Training...Epoch: 7
Epoch loss:  1.48498781919
Training...Epoch: 8
Epoch loss:  1.4077193141
Training...Epoch: 9
Epoch loss:  1.34389778078
Training...Epoch: 10
Epoch loss:  1.23470056951
Training...Epoch: 11
Epoch loss:  1.12658713758
Training...Epoch: 12
Epoch loss:  1.01056077778
Training...Epoch: 13
Epoch loss:  0.941288515925
Training...Epoch: 14
Epoch loss:  0.780876375735
Training...Epoch: 15
Epoch loss:  0.688878743351
Training...Epoch: 16
Epoch loss:  0.6400023669
Training...Epoch: 17
Epoch loss:  0.599933300912
Training...Epoch: 18
Epoch loss:  0.557211384177
Training...Epoch: 19
Epoch loss:  0.565168984234
Training...Epoch: 20
Epoch loss:  0.541655354202
Training...Epoch: 21
Epoch loss:  0.540477958322
Training...Epoch: 22
Epoch loss:  0.51386923492
Training...Epoch: 23
Epoch loss:  0.491514456272
Training...Epoch: 24
Epoch loss:  0.520187606663
Training...Epoch: 25
Epoch loss:  0.46363293156
Training...Epoch: 26
Epoch loss:  0.450173816085
Training...Epoch: 27
Epoch loss:  0.428997960687
Training...Epoch: 28
Epoch loss:  0.421355769038
Training...Epoch: 29
Epoch loss:  0.427983777225
Training...Epoch: 30
Epoch loss:  0.40272128135
Training...Epoch: 31
Epoch loss:  0.399276728183
Training...Epoch: 32
Epoch loss:  0.398895578086
Training...Epoch: 33
Epoch loss:  0.392715680599
Training...Epoch: 34
Epoch loss:  0.375555582345
Training...Epoch: 35
Epoch loss:  0.361774859577
Training...Epoch: 36
Epoch loss:  0.349185139686
Training...Epoch: 37
Epoch loss:  0.366207730025
Training...Epoch: 38
Epoch loss:  0.362537579983
Training...Epoch: 39
Epoch loss:  0.341955500841
Training...Epoch: 40
Epoch loss:  0.341290994734
Training...Epoch: 41
Epoch loss:  0.327200814337
Training...Epoch: 42
Epoch loss:  0.323004939407
Training...Epoch: 43
Epoch loss:  0.314804748446
Training...Epoch: 44
Epoch loss:  0.304103582352
Training...Epoch: 45
Epoch loss:  0.301586618274
Training...Epoch: 46
Epoch loss:  0.290632722527
Training...Epoch: 47
Epoch loss:  0.292472781986
Training...Epoch: 48
Epoch loss:  0.283731808513
Training...Epoch: 49
Epoch loss:  0.274497133493
Training...Epoch: 50
Epoch loss:  0.266947419941
Training...Epoch: 51
Epoch loss:  0.276129148901
Training...Epoch: 52
Epoch loss:  0.270186410844
Training...Epoch: 53
Epoch loss:  0.272461260855
Training...Epoch: 54
Epoch loss:  0.256774127856
Training...Epoch: 55
Epoch loss:  0.245880018547
Training...Epoch: 56
Epoch loss:  0.234373139217
Training...Epoch: 57
Epoch loss:  0.228528307751
Training...Epoch: 58
Epoch loss:  0.229470920563
Training...Epoch: 59
Epoch loss:  0.236886226758
Training...Epoch: 60
Epoch loss:  0.215278658643
Training...Epoch: 61
Epoch loss:  0.2126740098
Training...Epoch: 62
Epoch loss:  0.204833328724
Training...Epoch: 63
Epoch loss:  0.194522709772
Training...Epoch: 64
Epoch loss:  0.192005819827
Training...Epoch: 65
Epoch loss:  0.196523039043
Training...Epoch: 66
Epoch loss:  0.232590954006
Training...Epoch: 67
Epoch loss:  0.20532149151
Training...Epoch: 68
Epoch loss:  0.18971702531
Training...Epoch: 69
Epoch loss:  0.183923042938
Training...Epoch: 70
Epoch loss:  0.175981236994
Training...Epoch: 71
Epoch loss:  0.170480075479
Training...Epoch: 72
Epoch loss:  0.164054996893
Training...Epoch: 73
Epoch loss:  0.159125006199
Training...Epoch: 74
Epoch loss:  0.176349034533
Training...Epoch: 75
Epoch loss:  0.387349943817
Training...Epoch: 76
Epoch loss:  0.635446703434
Training...Epoch: 77
Epoch loss:  0.418017290533
Training...Epoch: 78
Epoch loss:  0.366075266153
Training...Epoch: 79
Epoch loss:  0.329099874198
Training...Epoch: 80
Epoch loss:  0.310989425331
Training...Epoch: 81
Epoch loss:  0.307675776631
Training...Epoch: 82
Epoch loss:  0.266403528303
Training...Epoch: 83
Epoch loss:  0.253842069954
Training...Epoch: 84
Epoch loss:  0.238983814418
Training...Epoch: 85
Epoch loss:  0.225468580797
Training...Epoch: 86
Epoch loss:  0.227900864556
Training...Epoch: 87
Epoch loss:  0.246425398812
Training...Epoch: 88
Epoch loss:  0.207749085128
Training...Epoch: 89
Epoch loss:  0.19795579277
Training...Epoch: 90
Epoch loss:  0.188621791452
Training...Epoch: 91
Epoch loss:  0.179104891792
Training...Epoch: 92
Epoch loss:  0.175652297959
Training...Epoch: 93
Epoch loss:  0.169657664001
Training...Epoch: 94
Epoch loss:  0.181949826702
Training...Epoch: 95
Epoch loss:  0.179353797436
Training...Epoch: 96
Epoch loss:  0.159280336276
Training...Epoch: 97
Epoch loss:  0.152446487546
Training...Epoch: 98
Epoch loss:  0.147212971374
Training...Epoch: 99
Epoch loss:  0.143081099913
Training...Epoch: 100
Epoch loss:  0.139548264071
Training...Epoch: 101
Epoch loss:  0.133973647654
Training...Epoch: 102
Epoch loss:  0.133898064867
Training...Epoch: 103
Epoch loss:  0.13686119467
Training...Epoch: 104
Epoch loss:  0.13933797814
Training...Epoch: 105
Epoch loss:  0.130110437796
Training...Epoch: 106
Epoch loss:  0.125812520273
Training...Epoch: 107
Epoch loss:  0.122239724174
Training...Epoch: 108
Epoch loss:  0.119406499714
Training...Epoch: 109
Epoch loss:  0.128934975341
Training...Epoch: 110
Epoch loss:  0.141922070086
Training...Epoch: 111
Epoch loss:  0.135050868616
Training...Epoch: 112
Epoch loss:  0.123463438824
Training...Epoch: 113
Epoch loss:  0.117116531543
Training...Epoch: 114
Epoch loss:  0.111001708545
Training...Epoch: 115
Epoch loss:  0.107865091227
Training...Epoch: 116
Epoch loss:  0.107620261796
Training...Epoch: 117
Epoch loss:  0.108155250736
Training...Epoch: 118
Epoch loss:  0.107103380747
Training...Epoch: 119
Epoch loss:  0.106201449037
```
