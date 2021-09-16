# **Python Application Development Using Luminoth** #
 <!--images-->
![Getting Started](luminoth.jpg)

Luminoth is a computer vision toolkit built in Python, using Google’s Machine Intelligence framework, TensorFlow and Sonnet.  Luminoth support object detection and image classification. It is a very useful library built by DeepMind for building complex neural networks with reusable components.

### Why Tensorflow (and why Sonnet)? ###
It is indisputable that TensorFlow is currently the most mature Deep Learning framework, and it offers a stable and production ready Machine Learning solutions.
Sonnet fits perfectly with the mission to build code that is easy to follow and to extend. It is tricky to build a computation graph that is abstract and low-level at the same time to allow building complex models, and luckily Sonnet is a library that provides just that.

### Installation and Use ###
All Luminoth dependencies will be downloaded automatically when you install Luminoth. However, Tensorflow, upon which Luminoth depends, provides two packages in PyPI: tensorflow (the CPU version) and tensorflow-gpu (the GPU version). Luminoth will default to the CPU version of the dependency. So, if you have a GPU, you should manually pre-install tensorflow-gpu before installing Luminoth by issuing: 
```{r, engine='shell', count_lines}
pip install tensorflow-gpu
```

Use pip to install Luminoth, by running the following command: 
```{r, engine='shell', count_lines}
pip install luminoth
```


After going through the installation process, the lumi CLI tool should be at your disposal. This tool is the main way to interact with Luminoth, allowing you to train new models, evaluate them, use them for predictions, manage your checkpoints and more.  Luminoth provides already-trained models so you can run predictions and get reasonable results in no time (and eventually be able to use them for fine-tuning). In order to access these checkpoints, we first need to download the remote index with the available models. Checkpoint management is handled by the lumi checkpoint subcommand.
Two checkpoints are present: 
-	 Faster R-CNN w/COCO (48ed2350f5b2): object detection model trained on the Faster R-CNN model using the COCO dataset. Aliased as accurate, as it’s the slower but more accurate detection model. 
-	SSD w/Pascal VOC (e3256ffb7e29): object detection model trained on the Single Shot Multibox Detector (SSD) model using the Pascal dataset. Aliased as fast, as it’s the faster but less accurate detection model.

Once the checkpoint is downloaded, it can be used for predictions. There are currently two ways to do this: 
-	 Using the CLI tool and passing it either images or videos. This will output a JSON with the results and optionally draw the bounding boxes of the detections in the image. 
-	 Using the web app provided for testing purposes. This will start a web server that, when connected, allows you to upload the image. Also useful to run on a remote GPU. (Note, however, that using Luminoth through the web interface is not production-ready and will not scale.)

Next steps would be to:
-	 Prepare your own dataset to be consumed by Luminoth. 
-	 Train a custom model with your own data, either locally or in Google Cloud. 
-	Turn your custom model into a checkpoint for easier sharing and usage. 
-	 Use the Python API to call Luminoth models within Python.

