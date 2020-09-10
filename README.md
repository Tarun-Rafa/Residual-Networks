# Residual Network
In this project, <a href="https://en.wikipedia.org/wiki/Residual_neural_network">Residual Network</a>, oftentimes abbreviated as ResNet is implemented in <a href="https://keras.io/">Keras</a>, which is a Python deep learning library. The purpose of this project is not to achieve high accuracy or to set new records for image classification tasks, but to showcase my programming skills in python. More specifically, the usage of programming frameworks such as Keras. Furthermore, as the name of the project suggests, I have implemented a residual neural network, introduced by <a href="https://arxiv.org/pdf/1512.03385.pdf">He et al.</a>, which is the default neural network architecture for very deep neural networks. In theory, very deep networks can represent very complex functions; but in practice, they are hard to train. Residual Networks, allows us to train much deeper networks than were previously practically feasible. This project is implemented as part of the <a href="https://github.com/adityachandupatla/deeplearning_coursera">deeplearning specialization</a> from Coursera.<br/>

<b>Note:</b> The original exercise required the students to implement image classification on a SIGNS dataset which included only 5 categories. But this project has been extended to support 10 categories (ranging from 0-9). Moreover, the dataset used during the course is different from the one used here.<br/>

As we can see, for very deep neural networks, the speed of learning decreases very rapidly for the early layers as the network trains. As a result, the network suffers from either <a href="https://en.wikipedia.org/wiki/Vanishing_gradient_problem">vanishing gradients or exploding gradients problem</a>.

<img src="https://github.com/adityachandupatla/residual_network/blob/master/images/vanishing_grad_kiank.png" />

<h2>Running the Project</h2>
<ul>
  <li>Make sure you have Python3 installed</li>
  <li>Clone the project to your local machine and open it in one of your favorite IDE's which supports Python code</li>
  <li>Make sure you have the following dependencies installed:
    <ol>
      <li><a href="http://www.numpy.org/">Numpy</a></li>
      <li><a href="https://www.tensorflow.org/">Tensorflow</a></li>
      <li><a href="https://keras.io/">Keras</a></li>
      <li><a href="https://pypi.org/project/pydot/">Pydot</a></li>
      <li><a href="https://www.scipy.org/">Scipy</a></li>
      <li><a href="https://matplotlib.org/">Matplotlib</a></li>
    </ol>
  </li>
  <li>Run resnet.py</li>
</ul>
If you find any problem deploying the project in your machine, please do let me know.

<h2>Technical Skills</h2>
This project is developed to showcase my following programming abilities:
<ul>
  <li>Python</li>
  <li>Computer Vision based applications</li>
  <li>Classification tasks</li>
  <li>Use of high level programming frameworks such as Keras</li>
  <li>Last but not the least, implementing the classical neural network architecture by He et al., ResNet!</li>
</ul>

<h2>Development</h2>
<ul>
  <li>Sublimt Text has been used to program the application. No IDE has been used.</li>
  <li>Command line has been used to interact with the application.</li>
  <li>The project has been tested on Python3 version: 3.6.1.</li>
</ul>

<h2>ResNet</h2>
<p><b>Dataset</b>: The dataset for this residual neural network is taken from <a href="https://www.kaggle.com/ardamavi/sign-language-digits-dataset/home">Kaggle</a>. The corresponding Github repository and further details regarding the dataset can be found <a href="https://github.com/ardamavi/Sign-Language-Digits-Dataset">here</a>. Sample images from the dataset:</p><br/>
<img src="https://github.com/adityachandupatla/residual_network/blob/master/images/dataset_preview.png" />
<p><b>Basic Idea</b>: In ResNets, a "shortcut" or a "skip connection" allows the gradient to be directly backpropagated to earlier layers:</p><br/>
<img src="https://github.com/adityachandupatla/residual_network/blob/master/images/skip_connection_kiank.png" />
<p>The image on the left shows the "main path" through the network. The image on the right adds a shortcut to the main path. By stacking these ResNet blocks on top of each other, we can form a very deep network.</p><br/>
<p><b>Architecture</b>: Two main types of blocks are used in a ResNet, depending mainly on whether the input/output dimensions are same or different. The identity block is the standard block used in ResNets, and corresponds to the case where the input activation (say  a[l] ) has the same dimension as the output activation (say  a[l+2] ). The upper path is the "shortcut path." The lower path is the "main path."</p><br/>
<img src="https://github.com/adityachandupatla/residual_network/blob/master/images/idblock3_kiank.png" />
<p>ResNet "convolutional block" is the other type of block. We can use this type of block when the input and output dimensions don't match up. The difference with the identity block is that there is a CONV2D layer in the shortcut path. The CONV2D layer in the shortcut path is used to resize the input  x  to a different dimension, so that the dimensions match up in the final addition needed to add the shortcut value back to the main path. For example, to reduce the activation dimensions's height and width by a factor of 2, you can use a 1x1 convolution with a stride of 2. The CONV2D layer on the shortcut path does not use any non-linear activation function. Its main role is to just apply a (learned) linear function that reduces the dimension of the input, so that the dimensions match up for the later addition step.</p><br/>
<img src="https://github.com/adityachandupatla/residual_network/blob/master/images/convblock_kiank.png" />
<p>The following figure describes in detail the architecture of this neural network. "ID BLOCK" in the diagram stands for "Identity block," and "ID BLOCK x3" means 3 identity blocks are stacked together.</p><br/>
<img src="https://github.com/adityachandupatla/residual_network/blob/master/images/resnet_kiank.png" />
<p><b>Results</b>:
  <ul>
    <li>ReLU activation has been used in all layers, except the last layer, where softmax activation has been used</li>
    <li>Adam optimizer with categorical crossentropy loss function has been used</li>
    <li>Number of training examples = 1649 and Number of test examples = 413</li>
    <li>The model has been trained for 10 epochs with a batch size of 32 on MacOS (with no GPU support)</li>
    <li>Total params: 23,608,202 Trainable params: 23,555,082 Non-trainable params: 53,120</li>
    <li>Train accuracy: 92.24% Test accuracy: 90.79%</li>
  </ul>
</p><br/>

Use this, report bugs, raise issues and Have fun. Do whatever you want! I would love to hear your feedback :)

~ Happy Coding
