# AI Terms

**Index**  

1. LLM (Large Language Model)
2. Tokenization
3. Vectors
4. Attention Mechanism

---

## #1 LLM (Large Language Model)

LLM is - a neural network that is trained to predict the next term of an input sequence.  

For example,

Try the following examples and observe the output produced by LLM.

Input - "All that glitters"

Input - "Roses are red"

---

## #2 Tokenization

This has to do with processing the input of a Large Language Model (LLM).  

For example when you pass the following phrase to LLM:  

All that glitters  

The first thing that LLM is going to do is -  
break this into discrete tokens.  

The core problem for the Large Language Model is to truly understand  
human language so that it can speak it really well.  

And this start with Tokenization.

Input  ---->  LLM - Tokenization  ---->  A list of tokens

---

## #3 Vectors

Tokens tell you what you should focus on.  
What is the smallest term that you can derive meaning from?  

But what meaning has to be derived is represented by Vectors.

If the Large Language Model can map a two dimensional or an N dimensional space  
such that all the words which are close in meaning are placed close to each other,  
then the benefit will be that the meaning of these words will be turned into a coordinate.

This is called a Vector.

The coordinate, the mapping of a word in an N dimensional space such that  
near by words, similar meaning words are all clustered together and  
opposite meaning words are somewhere far away,  
comes through the process of vectorization.

The end result of this is that Large Language Models know the inherent meaning  
of all the words that are in the English vocabulary,  
and they also know how to break it into small tokens.  

Words which are similar to each other are placed close to each other.  

Once they know the meaning, they can construct sentences effectively.  

---

## #4 Attention Mechanism

Lets take the following example:  

* "Tasty Apple" - you are probably talking about Apple fruit
* "Apple's Revenue" - you are probably talking about Apple company
* "The apple of my eye" - you are probably talking about a young person who you have affection for

So here we have the same word "Apple" but it has different meaning.  

Only way to understand the meaning is not by looking at the word itself,  
but by looking at nearby/surrounding words, they add context to the meaning of "Apple".  

LLMs can derive meaning this way now.  
The way they do it is by looking at the nearby words in a sentence.  
Generate those vectors - Nearby Contextual Vectors.
And for ambiguous terms you end up with Ambiguous Vectors.

"Apple's Revenue"  

Nearby Contextual Vectors - v_revenue  
Ambiguous Vectors - v_apple  

```
v_revenue
    |
    |
    + Attention
    |
    |
v_apple

and then this is pushed into the direction of company Apple,  
where other similar vectors are like Google, Meta, Amazon, Microsoft etc.
```

"Tasty Apple"  

Nearby Contextual Vectors - v_tasty  
Ambiguous Vectors - v_apple  

```
v_tasty
    |
    |
    + Attention
    |
    |
v_apple

and then this is pushed into the direction of fruit Apple,  
where other similar vectors are like Banana, Pineapple, Chiku, Guava etc.
```

so you can tokenize input text,  
derive the inherent meaning of all those tokens,  
and for ambiguous tokens, for tokens which are difficult to understand,  
you have a mechanism to add context by looking at nearby words.  

Because LLM is able to derive contextual meaning,  
it is able to construct sentences in a way that humans speak.  

---

## #5 Self-Supervised Learning

How do you train LLM to predict the next token?  

Instead of telling the model exactly what it needs to do,  
the structure of the input data is such that the model knows what it should do.  

A section of the input can be predicted, even if you make that section blank.  

Which means that there is inherent structure in your input  
which your brain/LLM is able to replace with the expected token/output.  

Standard way to train such a model would be called supervised learning,  
where you would have a human being say that - 

if the input text is "All that glitters",  
then the model should predict/output "is not Gold.".  

if the input text is "Et tu",  
then the model should predict/output "Brutus.".  

Instead Self-Supervised Learning has made getting test data much cheapter here.  

Here if you have "Et tu Brutus.",  
then the model is going to be fed in this text  
and it is going to make 3 predictions:  
1. "Et" - What comes after "Et"?
1. "Et tu" - What comes after "Et tu"?
1. "Et tu Brutus." - What comes after "Et tu Brutus."?

No humans are involved here.  
You had some text in the world.  
Maybe you scraped this off the internet and now you are telling the model:  
Look, I have 3 questions for you. Tell me, what are the right answers?  

So the model looks at these three puzzles.  
And it tries to make prediction for each of them.  

Now the model makes mulitple predictions for each of them,  
it is rewarded for the correct response and penalized for mistakes (increases LOSS).  
Model is trained to provide correct response.  
And Neural Network weights are updated.  

What you are doing is - you are looking at text which already exists in the world,  
and you are creating multiple challenges for yourself without human intervention.  
This is what makes the model self-supervised.  

Raw Data (source internet or other) -> LLM -> Creates Multiple Challenges -> Predictions -> Reward for Right, Penalty for Wrong/Mistake -> Neural Network weights are updated

This makes LLM really really scalable.  

Most AI models now are moving to self-supervised learning.  

---
