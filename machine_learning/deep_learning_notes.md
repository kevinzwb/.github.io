# Linear Regression

### Logistic Regression For Classification
Find a linear hyperplane to separate the data, better that output the probability of class

- Linear model: $$z(\boldsymbol{w},\boldsymbol{x}) = \boldsymbol{w} \cdot \boldsymbol{x}$$

- Link Function: $$\hat{p}(z) = \frac{1}{1 + exp(-z)}$$

- Cross entropy loss: $$l(y,\hat{p}) = ylog\hat{p} + ( 1 - y )log(1 - \hat{p} )$$

- Cost Function: $$ L(\boldsymbol{w},\{\boldsymbol{x}_i,y_i\}^m_{i=1} )= \sum^m_{i =1} log(1 + exp(\boldsymbol{w} \cdot \boldsymbol{x}_i)) - y_i\boldsymbol{w} \cdot \boldsymbol{x}_i$$

- Gradient: $$ \nabla_w  L(\boldsymbol{w},\{\boldsymbol{x}_i,y_i\}^m_{i=1} ) = (\frac{1}{1 +  exp(-\boldsymbol{w} \cdot \boldsymbol{x}_i)}- y_i)\boldsymbol{x}_i $$

The backpropagation algorithm works through the layers of deeper neural networks to calculate error gradients w.r.t to weights

# Convolutional Networks
![index](https://github.com/kevinzwb/kevinzwb.github.io/raw/master/machine_learning/figures/CNN_Networks.png)




# Sequences and Recurrent Neural Nets
Nerual Nets struggle with sequences because inputs and outputs must be fixed-sized vectors

### Long Short-Term Memory
![LSTM](https://github.com/kevinzwb/kevinzwb.github.io/blob/master/machine_learning/figures/LSTM.png)
- $$ i_t = W_{ix}x_t + W_{ih}h_{t-1} + b_i $$
- $$ j_t = W_{jx}x_t + W_{jh}h_{t-1} + b_j $$
- $$ f_t = W_{fx}x_t + W_{fh}h_{t-1} + b_f $$
- $$ o_t = W_{ox}x_t + W_{oh}h_{t-1} + b_o $$
- $$ c_t = \sigma(f_t) \odot c_{t-1} + \sigma(i_t) \odot tanh(j_t) $$
- $$ h_t = \sigma(o_t) \odot tanh(c_t) $$


# Attention and Memory in Deep Learning
The ability to focus on one thing and ignore others has a vital role in guiding cognition.
Deep nets naturally learn a form of implicit attention where they respond more strongly to some parts of the data than others.

RNNs contain a recursive hidden state and learn functions from sequences of inputs to sequences of outputs.
The sequential Jacobian shows which past inputs they remember when predicting current outputs.

The benefits of explicit attention mechanism:
- Computational efficiency
- Scalability 
- Sequential processing of static data
- Easier to interpret
The network produces an extra set of outputs used to parameterise an attention model. 
The attention model then operates on some extra data to create a fixed-size glimpse that is passed to the network as an extra input at the next time step. 

Attention models generally work by defining a probability distribution over glimpses **g** of the data **x** and some set of attention outputs **a** from the network, that is $$ Pr(g|a) $$
We then use the attention parameters **a** to determine a distribution Pr(g|a) only by taking an expectation over all possible glimpses instead of a sample $$ g = \sum_{g' \in x }g'Pr(g'|a) $$


### Neural Turing Machines
Introspective attention: with internal information we can do selective writing as well as reading, allowing the network to iteratively modify its state
![Turing_Machines](https://github.com/kevinzwb/kevinzwb.github.io/blob/master/machine_learning/figures/Turing_Machines.png)




