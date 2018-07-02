Sequence prediction Problem

Sequence predicition is different from other supervised learning problems. The sequence imposes an order on the observations that must be present when training a model and making predictions. Generally , prediction problems that involve sequence data are referred to as sequence prediction problems. Sequence of data refer to data that comes in a time based order that is one after the other.
The sequence problem can be divided into 4 differennt types :
1. Sequence Prediction.

2. Sequence classification

3. Sequence Generation

4. Sequence to sequence prediction.

# Sequence Prediction :-

Sequence and Sets :-
In Applied ML it is often required that we deal with sets such as train and test samples.Each observation on the set can be thought of an observation in the domain. In a set the order of the observation is not essential. However , the sequence the order of the observation is explicit and important.So sequence have order that is essential. 

Sequence Prediction :
Sequence Prediction involves predicting the next value in the given input sequence for example
input Sequence: 1,2,3,4,5
Output Sequence: 6.

Sequence prediction is also called sequence learning

examples :-
weather forcasting : Given the weather details over time predict the weather of tomorrow. 
Stock market price forcasting : Given the stock movement in the past predict the movement going forward.
product recommendation : Given a list of past purchases of the customer , predict the next purchase.

Sequence Classification :
Sequence Classification involves predicting the class labels for a given input sequence.

Input Sequence : 1,2,3,4,5
Output : "good"

the objective of the sequence classification is to build a classification model based on the labelled dataset.So that the model can predict the class of the unknown sequence.

The sequence classification deals with both the real value and discrete sequence classification. The discrete classification
involves classification problems like 
DNA sequence classification : given a sequence of DNA A, C,G,T predict the sequnce is for coding or non-coding.
Anomaly Detection : given a sequence of observation , predict whether the sequnce is anamolous or not.
Sentiment Analysis : Given a sequence of text predict whether the sentiment os positive or negative.


Sequence Generation :-
sequence generation involves generating a new sequence that has the same general characteristics as the other sequence in the corpus .
Input sequence : [[1,3,5],[7,9,11]] 
Output Sequence : [3,5,7]

Some examples include : 
Text generation : Given a corpus of text generate a new sentence or paragraphs of text that read as if drawn from the corpus.
Handwriting Prediction : Given a corpus of handwriting examples , generate handwriting for new phrases that has the properties of the handwriting in the corpus.

Hand writing prediction : Given a corpus of handwriting examples , generate handwriting for new phrases that has the properties of handwriting in the corpus.

Music  Generation : Given a corpus of examples of music generate a new musical piece that have the properties of the corpus.
Image caption generation : is also an example of the sequence generation.However here we have only one input sequence and based on it we predict the textual description of the image.

Input : ["image pixels"]
Output : ["written description"]


Sequence -to- sequnce Prediction :
Seq-2-Seq prediciton involves an output sequence given an input sequence for example:
Input : 1,2,3,4,5
Output : 6,,7,8,9,10

"Despite the flexibility and power of Deep neural network can only be used for problems whose inputs and targets can sensibly encoded with vectors of fixed dimensionality. It is significant , limitation , since many problems are best expressed with Sequence whose lengths are not known a -priori. For example : speech recognition , machine translation , question answering . seq2seq model at its core is an extension of exisitng  Sequence model where , rather than predicting a single next value in the sequence , a new Sequence is predicited that may not be the same length as that of the original input value. seq2seq learning at its core , uses recurrent neural network to map _variable -length_ input sequence to variable length output sequence for example in neural machine translation."

exampe uses : 
1. text summarization
2. multi step time series Forecasting : Given a series of observation , predict a Sequence of observation for a range of future time steps.
3. Program Execution : Given the textual description program or mathematical equation predict the sequnce of characters that describes the correct output.

# Advantages of Multi-layer Perceptrons :
Classical neural neteork called multi layer perceptron or MLP for short can be applied to Sequence predicition problems.MLP approximate function a mapping functiion from input variables to output variables. This general capability is important for Sequence prediction problems (notably the time series forecasting) for a number of reasons.

# Robust to Noise. Neural Network are robust to noise in input data and in the mapping function and can even support learning 
and prediction in the presence of missing values.
Nonlinearity : neural Network do not make a strong assumptions about the mapping function and readily learn linear and non linaer relationships.

Specifically an MLP can be configured to support an arbitraily defined but _fixed number_ of inputs and outputs in the mapping function.

# multi variate inputs : An arbritary number of inputs features can be specified , provided direct support for multivariate prediction

# multi step outputs an arbritary number of output values can be specified , provided direct support for multi-step and even multivariate prediction.

# the applicatiion of MLP to Sequence prediction requires that the input sequnce be divided into smaller overlapping subsequnces that are shown to the network in order to generte a predicition.

# Limitation of MLP

@ Stateless 
@ Unaware of Temporal Structure : time steps are modeled as input features , meaning that netwok has no explicit handling or understanding of the temporal structure or order between the observations.
@ Messy Scaling
@ Fixed input Size  : The size of the input window is fixed and must be imposed in all inputs in the system
@ Fixed output Size. The size of the output is fixed and the output that donot conform to the fixed output size needs to be forced.

Hence the basics issue with the MLP is that we have to specify the scope of temporal dependence between observations explicitly upfront in the design of the model.

# Promises of the Recurrent Neural Network
the LSTM or long Short Term Memory or LSTM network is a typ of Recurrent Neural Network . A RNN is a special neural network designed for srequence problems . Given a standard feed forward network MLP , an RNN can be thought of as addition of loops in the architecture. For example in an RNN in any given layer each neuron passes its signal laterally (sideways) in addition to forward to the next layer.The output of the network may feedback as an input to the network with the next input vector.
























