#Part 1 

## Screenshot of backprop working file 
<img width="835" alt="image" src="https://github.com/adishukla2009/ERA-V1/assets/1230195/8f8c1747-827f-40ee-9a93-6cb90c065642">

## Major steps 
      1- Firstly we calculate the value of hidden layers, the activation output of each layer and then calculate loss - Loss is the difference from target and is having the 1/2 to help with the maths. Also the activation function used is Sigmoid. This helps with implementation on excel sheet
      2- Next up we start calculating the partial derivatives using the chain rule - DE total/DW5 which becomes DE1 / DW5 since E2 is not dependent on W5 
      3- DE1/DW5 is calculated by multiplying DE1/DA_o1 * DA_o1/D_o1 * D_o1/DW5
      4 - Placing the value of each term we get the below 
                                                        ∂E_total/∂w5 = (a_01 - t1) * a_o1 * (1 - a_o1) *  a_h1					
                                                        ∂E_total/∂w6 = (a_01 - t1) * a_o1 * (1 - a_o1) *  a_h2					
                                                        ∂E_total/∂w7 = (a_02 - t2) * a_o2 * (1 - a_o2) *  a_h1					
                                                        ∂E_total/∂w8 = (a_02 - t2) * a_o2 * (1 - a_o2) *  a_h2		
      5- Now moving to the next layer - Both E1 and E2 would be dependent on A_h1 and A_h2 - so we have to caluclate DE1/DA_h1 and DE2/DA_h1 and add them to get the value for DE total / DA_h1 - As seen below 
                                                        ∂E1/∂a_h1 = (a_01 - t1) * a_o1 * (1 - a_o1) * w5								
                                                        ∂E2/∂a_h1 = (a_02 - t2) * a_o2 * (1 - a_o2) * w7								
                                                        ∂E_total/∂a_h1 = (a_01 - t1) * a_o1 * (1 - a_o1) * w5 +  (a_02 - t2) * a_o2 * (1 - a_o2) * w7								
                                                        ∂E_total/∂a_h2 = (a_01 - t1) * a_o1 * (1 - a_o1) * w6 +  (a_02 - t2) * a_o2 * (1 - a_o2) * w8	
                                                        
                                                        
       6- Again using chain rule - 
                                                        ∂E_total/∂w1 = ∂E_total/∂a_h1 * ∂a_h1/∂h1 * ∂h1/∂w1					
                                                        ∂E_total/∂w2 = ∂E_total/∂a_h1 * ∂a_h1/∂h1 * ∂h1/∂w2					
                                                        ∂E_total/∂w3 = ∂E_total/∂a_h2 * ∂a_h2/∂h2 * ∂h2/∂w3				
                                                        
        7 Finally putting all the values 
                                      ∂E_total/∂w1 = ((a_01 - t1) * a_o1 * (1 - a_o1) * w5 +  (a_02 - t2) * a_o2 * (1 - a_o2) * w7) * a_h1 * (1 - a_h1) * i1	
                                      ∂E_total/∂w2 = ((a_01 - t1) * a_o1 * (1 - a_o1) * w5 +  (a_02 - t2) * a_o2 * (1 - a_o2) * w7) * a_h1 * (1 - a_h1) * i2				
                                      ∂E_total/∂w3 = ((a_01 - t1) * a_o1 * (1 - a_o1) * w6 +  (a_02 - t2) * a_o2 * (1 - a_o2) * w8) * a_h2 * (1 - a_h2) * i1			
                                      ∂E_total/∂w4 = ((a_01 - t1) * a_o1 * (1 - a_o1) * w6 +  (a_02 - t2) * a_o2 * (1 - a_o2) * w8) * a_h2 * (1 - a_h2) * i2			
         8- Now the subsequent weights are calculated by using learning rate and the partial derivative for loss with respect to that particular weight 
         
         
         ## How does the loss change with different leaning rates 
         
         A - η =0.1 , The loss change is linear from 0.014181378 to 0.009572139 its learning but at a very slow pace 
         B - η =0.2 , The loss change is from 0.014181378 to 0.006369969 its learning but at a very slow pace, its better than earlier 
         C - η =0.5 , The loss change is from 0.014181378 to 0.001782022 its better than earlier and now we can see a definite curve with gradient being steep till half way and thenm tapering
         D- η =0.8 , The loss change is from 0.014181378 to 0.000478649
         E -η =1 , The loss change is from 0.014181378 to 0.000196838 - Its reaching almost 0 in 68 runs 
         F - η =2  The loss change is from 0.014181378 to 2.09236521683586E-06 - Its reaching almost 0 in 39 runs
         G - η =10 - It learned very quickly - reaching almost zero loss in 7 runs 
         H - η =100 - The loss jumped to .08 from .014 and then it showed to local maximas before reaching almost 0 loss by 37 runs 
         I -η =500 - The loss graph creates an M with max loss going to 0.25 twice and then returning to 0 in about 20 runs 
         J - η =1000 - The loss increase to 0.25 and stays the same - the model is not learning 
         
         



                                      
                                      
                                     


    
          






















# Part 2
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
