## The Task at hand was - on the MNIST dataset Acheive 99.4% validation accuracy with Less than 20k Parameters Less than 20 Epochs No fully connected layer

Firstly, I started with the main goal of reduction of parameters while keeping the max channels and the minimum required receptive field before the Max pooling layer
*I found that 16 is the optimum number of channels and the receptive field as 5* - before we went in for max pooling( Visualize MNIST dataset - we can start seeing edges appearing after 5 pixels so that was a good place to start)
Relu, Batch norm and Droput were used for each layer

Batch norm was not recommended to be used before last layer ( I tried using but still got 99.46% accuracy but removed in the later tries)
Relu was not performed on the last layer

I experimented with the learning rate starting from .001 and going to .01 ( Turns out .01 was the best )
Then I tried to change the batch size to 64 but was not getting any better results, so I stuck with batch size as 128

Results
Params Used - 19,642
Epochs - 20
Validation Accuracy - 99.42%
