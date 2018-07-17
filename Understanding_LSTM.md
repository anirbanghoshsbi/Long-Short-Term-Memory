# Recurrent Neural Network

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

# Writing a children's book :

Let us a say we are writing a children's book.
The book has "Doug saw Jane. Jane saw Spot. Spot Saw Doug."

My Book has just three lines and has a vocabulary of {Doug , Jane , Spot , saw .}.
The task of the neural network is to find what is the nest word given this sequence 
of words.


