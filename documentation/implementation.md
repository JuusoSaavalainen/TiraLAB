# Recognition of Handwritten Numbers

##  Goal
To be able to train your custom neural network , and test the model in practice

## Model

The model implementation is a Deep Neural Network (DNN) built from scratch using NumPy, with the MNIST database as the data source. The network architecture is designed to be modular, allowing for exploration of different layer configurations and hyperparameters. The current implementation that is used in GUI uses a 5-layer setup, with fully connected layers, making it a Multilayer Perceptron (MLP). 

In the model many things are used but the main ones are backpropagation , forwardpropagation, onehot encoding, softmax, relU (also derived), sigmoid (also derived), and gradient descent with batching. Most of the data is stored in dicts containing numpy arrays.

## GUI

For those who do not wish to explore the training process or the modularity of the model, there is a Tkinter-based GUI provided for testing the pretrained model. The GUI allows the user to draw their own digits, which are then inputted to the model for prediction. The current implementation may not be optimal, but with properly centered drawings, the accuracy is quite high. Improving the centering algorithm for the input images could further increase the accuracy of the model. In GUI opencv libary is used for blurring the images. Pictures that are taken from the gui canvas should be close as possible to original mnist data for the best result. Blurring or smoothening the pixels is one step towards that. Centering of the pictures is something that should improve the model afterall (#TODO). 

## Training (CLI)
*only mvp avaible work in progress*

If desired, the model can be trained with custom parameters. The process involves cloning the repository and using Poetry to install dependencies and run the training CLI. The `idx_to_csv.py` file must be runned with the `dowloadmnist` with Poetry. Once the CSV files are obtained the training CLI can then be run with `poetry run invoke train`.  

In the training you can choose custom values to these parameter:
- *Number of hidden layers* [positive number]
- *Size of those layers* [postive number]
- *learning rate* [positive number]
- *Epochs* [positive number]
- *Batch size* [positive number] 
- *Activation function* [relU, sigmoid]

Training type could also be customize able. 

## Comparison
Comparision is done with these base settings : Relu, 20 epocs, batch size = 10, learning rate = 0.03.
In the comparision both have 1 hidden layer one with 10 nodes one with 100 nodes second is allways the on with 100:

![10 nodes](https://github.com/JuusoSaavalainen/Neural-network-with-numpy/blob/main/documentation/acc2010.png)
![100 nodes](https://github.com/JuusoSaavalainen/Neural-network-with-numpy/blob/main/documentation/acc20100.png)
![10 nodes](https://github.com/JuusoSaavalainen/Neural-network-with-numpy/blob/main/documentation/loss2010.png)
![100 nodes](https://github.com/JuusoSaavalainen/Neural-network-with-numpy/blob/main/documentation/loss20100.png)

### The training time of a single epoch is heavily affect by these factors
- Number and size of the layers. Its clear that more nodes and more layers will result in slower training loop as the steps on the back and forward propagation increases more np.dots will be calculated and the training loop slows down

- The batch size speeds up the training as it increases. Resulting in a lower number of calculations for each epoch. 


