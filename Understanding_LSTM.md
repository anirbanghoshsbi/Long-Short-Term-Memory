# Recurrent Neural Network (Long Short Term Memory)

Recurrent Neural Networks are a good example of algorithms that can be used for sequence problems. By Sequence problem , I mean anything that 
has a time factor attached to it.

For example : text , speech , audio , video  or share price prediction or anything that can be shown as time factor attached to it.

In order to understand this problem let us take the example of what is for dinner?
Suppose I get either Bread , Rice , Pizzas alternatively every night. I have no other choice but to eat only one of these and every night.

Now in order to predict what would I eat tonight I might try to build a Neural Network. The Neural Network that I build takes in a number 
of factors into account like "Day of the Week" , "How was my day" , "My energy level" , "Whether I had slept properly or not the previous 
night" , etc. However , inspite of these variables and a number of hyper parameter tuning I find that the Neural Network is unable to 
correctly predict what I woud eat that night. The best it does is 33.33%.

So the neural network is missing something? The missing part of the puzzle is I have not considered the relation between the three dinner
that I am allowed to have, that is Bread , Rice , Pizza.There is a pattern : _I always eat Bread , Rice , Pizzas in this order only!._ 
The previous Neural Network took everything into account but the inherent relation between the data which is sequential. Sequential data means there is some 
inherent relation between the pattern of data being fed into the system and the system is required to filter out this inherent relation.

Now , if this criteria that I eat _Bread-Rice-Pizza_ in this sequence, is given as feature to our Neural Network then , this becomes a
very easy problem. The only variable that my system needs to focus on is the what did I eat yesterday to figure out what I would eat today.

Now the issue that bothers me how do I feed this information to the Neural Network. The Neural Network runs in a computer and everything that
the computer understands is _Ones and Zeros_. To solve the problem we can bring in the concept of Vector.

A Vector is a fancy name for a list. Suppose the weather today is 

```
High Temperature : 38 Deg
Low Temperature : 24 Deg
Wind : 13 kmph
precipatation : 0.15 mm
Relative Hunidity : 84% , then ,
the weather vector is |38|24|13|0.15|84|.
So Vector is a series of number to represent a phenomena like today's weather.
```

>Anything that goes into the computer is first converted into a list of numbers before it goes through it.

Now if I say today is tuesday :
It can also be coded into number like so:
Tuesday -->0100000 (0 for all days of a Week and 1 for Tuesday.)
These kind of sparse matrices are called One Hot Encoded Vector , though they look cumbersome but are very useful for 
reprsenting _categorical data_ to computer.

Coming back to the idea of dinner , the food I am having Bread , Rice , Pizza are all categorical data and can be one hot encoded 
so that the computer can understand it easily.
```
So let Bread be  100
Similarly Rice be 010
and the Pizza be 001
```

Now whenever my Neural Network finds that I have eaten Rice yesterday , it predicts that I would have Pizza today. However , now let us 
consider a caveat , yesterday I was out of town so I didnot eat the usual food yesterday so how the system would predict what would I eat
today. Here comes the _time_step_ criteria.

Assuming the time_step in our situation is 1 day back. So it means that my neural network not only remembers what I ate yesterday but also
what I ate day before yesterday.

So if I skipped dinner yesterday , but day before yesterday had Pizza then it knows I should eat Rice today as I should have eaten 
Bread yesterday ,which I missed but then I follow the schedule meticulously and would eat Rice only!

> These time steps or the ability of the neural network to remember things in past for a fixed number of time steps is called 
>Back Propagation through Time.


# Writing a Children's Book
Suppose a Children Book has the following lines

Doug saw Jane.
Jane saw Spot.
Spot saw Doud.

Then the dictionary that is formed is 

{Doug , Jane ,Spot,saw,.} these are the unique words and the dictionary is formed of these words only.Our Network Needs to _learn_
the pattern in sequence of the data in dictionary._So if I have the most recent word as Doug then the network should propose the most frequent word as either saw or . as these are the most frequent word to follow after a name._

Now let us assume that the Neural Network Predicts that the word after Doug is _saw_ now the Network needs to make the next prediction and it is now a name as probablistically it is evident that after the word saw we normally the NN gives a name say either Doug , or Jane or Spot. 
But the issue arises when we have a Doug saw Doug prediction. The LSTM allows to prevent mistakes like these with its multiple neural networks each for a particular task say selection, forgetting or ignoring etc. which prevents issues like Doug saw Doug kind of issues.The LSTM Neural Network can hold on to the predictions for future , if my time step is 1 then the Network will remember that _yesterday it had predicted Doug today It predicted saw_  so tomorrow's prediction will certainly include the fact yesterday I predicted saw and on day before yesterday (t+1) had predicted Doug so , it should not predict a Doug or saw but the other names like Spot or Jane.

# How Does LSTM perform the above feat?
1.The LSTM does have the ability to remove or add information to the cell state, carefully regulated by structures called gates.
Gates are a way to optionally let information through. They are composed out of a sigmoid neural net layer and a pointwise multiplication operation.
2. The core reason that recurrent nets are more exciting is that they allow us to operate over sequences of vectors: Sequences in the input, the output, or in the most general case both.[One --> One] ,[One-->Many] , [Many-->Many] ,[Many-->Many].This overcomes the  glaring limitation of Vanilla Neural Networks : they accept a fixed-sized vector as input (e.g. an image) and produce a fixed-sized vector as output (e.g. probabilities of different classes). Not only that: These models perform this mapping using a fixed amount of computational steps (e.g. the number of layers in the model).

# Examples of Sequences :

# Sequence Prediction:
Suppose I have numbers 1,2,3,4,5,6 then the NN needs to provide the next item in the list which in our case is 7.

[1,2,3,4,5,6] --[Model]--> [7] as the output.

Some examples of sequence prediction problems include:
1.Weather Forecasting. Given a sequence of observations about the weather over time,predict the expected weather tomorrow.
2.Stock Market Prediction. Given a sequence of movements of a security over time,predict the next movement of the security.
3.Product Recommendation. Given a sequence of past purchases for a customer, predict the next purchase for a customer.

# Sequence Classification:

[1,2,3,4]--[Model]--> [Good]

The objective of sequence classification is to build a classification model using a labeled dataset [...] so that the model can be used to predict the class label of an unseen sequence.

Examples :

1.DNA Sequence Classification. Given a DNA sequence of A, C, G, and T values,predict whether the sequence is for a coding or non-coding region.
2.Anomaly Detection. Given a sequence of observations, predict whether the sequence is anomalous or not.
3.Sentiment Analysis. Given a sequence of text such as a review or a tweet, predict whether the sentiment of the text is positive or negative.

# Sequence Generation :
Sequence generation involves generating a new output sequence that has the same general characteristics as other sequences in the corpus
example [[1,3,5],[7,9,11]--[Model]--> [3,5,7].

Uses of Sequence Generation
1.Text Generation. Given a corpus of text, such as the works of Shakespeare, generate new sentences or paragraphs of text that read they could have been drawn from the corpus.
2.Handwriting Prediction. Given a corpus of handwriting examples, generate handwriting for new phrases that has the properties of handwriting in the corpus.
3.Music Generation. Given a corpus of examples of music, generate new musical pieces that have the properties of the corpus.

# LSTMS in details 

LSTM Weights:
A memory cell has weight parameters for the input, output, as well as an internal state that is built up through exposure to input time steps.
1.Input Weights. Used to weight input for the current time step.
2.Output Weights. Used to weight the output from the last time step.
3.Internal State. Internal state used in the calculation of the output for this time step.

LSTM Gates
The key to the memory cell are the gates. These too are weighted functions that further govern the information flow in the cell. There are three gates:
1.Forget Gate: Decides what information to discard from the cell.
2.Input Gate: Decides which values from the input to update the memory state.
3.Output Gate: Decides what to output based on input and the memory of the cell.

The forget gate and input gate are used in the updating of the internal state. The output gate is a final limiter on what the cell actually outputs, (and is responsible for preventing _Doug saw Doug_ kind of Prediction).

# Advantage of LSTM :
 1.Overcomes the technical problems of training an RNN, namely vanishing and exploding gradients.
2.Possesses memory to overcome the issues of long-term temporal dependency with input sequences.
3.Process input sequences and output sequences time step by time step, allowing variable length inputs and outputs.

