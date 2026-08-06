# AI Terms

**Index**  

1. LLM (Large Language Model)
2. Tokenization
3. Vectors
4. Attention Mechanism
5. Self-Supervised Learning
6. Transformer
7. Fine Tuning
8. Few-Shot Prompting OR Example in Prompt
9. RAG (Retrieval Augmented Generation)
10. Vector DB
11. MCP (Model Context Protocol)
12. Context Engineering
13. Agents
14. Reinforcement Learning
15. Chain of Thoughts

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
* "Apple's Revenue" - you are probably talking about Apple company's revenue
* "The apple of my eye" - you are probably talking about a young person who you have affection for

So here we have the same word "Apple" but it has different meaning in different context.  

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
```

and then this is pushed into the direction of company Apple,  
where other similar vectors are like Google, Meta, Amazon, Microsoft etc.

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
```

and then this is pushed into the direction of fruit Apple,  
where other similar vectors are like Banana, Pineapple, Chiku, Guava etc.

So you can tokenize input text,  
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

A section of the input can be predicted, even if you make that section blank/hidden.  

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

## #6 Transformer

Transformer X LLM  
Transformer is NOT LLM.  

LLM predicts the next token for the given input sequence.  
Transformer does the same thing but it is a specific algorithm or a specific method by which  
you predict the next token.

So think of it this way - LLM is a car and Transformer is an engine.  

LLM can use different algorithm then Transformer.  

---

## #7 Fine Tuning

When a base model is trained to answer in a specific way, it is called Fine Tuning.  

To fine tune a base model on finance domain,  
it is trained on a series of questions and answers of the finance domain.

To fine tune a base model on medical domain,  
it is trained on a series of questions and answers of the medical domain.

Internal weights of the model are updated and that way model will learn a particular domain.  

This is like specializing in a domain.  

Analogy  
Up to 10th every student studies the same.  
After that students have choice to choose from "Arts", "Commerce" or "Science" stream.  
Then again after 12th they have more choices of courses to specialize in their domain of interest.  

---

## #8 Few-Shot Prompting OR Example in Prompt

Think of **Few-Shot Prompting** like showing a new assistant a few filled-out forms before asking them  
to fill out a new one. Instead of just describing what you want through instructions, you provide explicit  
**input -> output pairs or examples** directly inside your prompt.

This is incredibly useful when you want a highly specific format, a particular tone,  
or a precise logical structure that is hard to explain with text instructions alone.

Here are two practical examples showing how it works:

---

### Example 1: Standardizing Technical Error Log Analysis

Imagine you are building a tool to parse ugly system crashes into a clean, structured JSON format  
for your team's tracking system.

**The Few-Shot Prompt:**

```text
You are a system monitoring assistant. Convert raw server error logs into a clean JSON format 
following these exact examples.

### Example 1
Input log: [2026-07-19 14:22:01] ERROR auth_service.js line 42: Connection timed out to DB cluster-primary-01 after 5000ms.

Output JSON:
{
  "service": "authentication",
  "severity": "high",
  "issue": "Database connection timeout",
  "target_resource": "cluster-primary-01"
}

### Example 2
Input log: [2026-07-19 14:25:30] WARN file_store.go line 118: Disk space utilization at 87% on /dev/sdb3.

Output JSON:
{
  "service": "storage",
  "severity": "medium",
  "issue": "High disk space utilization",
  "target_resource": "/dev/sdb3"
}

### Now do this one:
Input log: [2026-07-19 15:02:12] ERROR payment_gateway.py line 89: Failed to post payload to external vendor API stripe_v3, server returned 502 Bad Gateway.

What will be the "Output JSON"?
```

**Why it works:** Instead of trying to write a complex rule like *"If the log says payment_gateway, set service to billing or payment, and map vendor strings to target_resource,"* you simply show the model two clean examples. The model picks up on the pattern, mapping `payment_gateway.py` to a `"payment"` service and extracting `stripe_v3` perfectly.

---

### Example 2: Adhering to a Strict "Brand Voice" and Format

Suppose you need an LLM to generate release notes or feature updates for a product,  
but it *must* follow a very specific micro-format: a punchy headline, a one-sentence user benefit,  
and a technical detail tag.

**The Few-Shot Prompt:**

```text
Write a short product update notification for the user dashboard based on the raw feature description provided.
Follow the exact style, tone, and format of the examples below.

### Example 1
Raw feature: We added a dark mode toggle to the user profile settings page because people kept asking for it for night coding.

Update:
🚀 **Night Owls Rejoice: Dark Mode is Live!**
You can now ease eye strain during late-night coding sessions by toggling the new Dark Mode directly from your Profile Settings.
*Tag: UI/UX | Frontend*

### Example 2
Raw feature: The database migration team optimized the primary keys on the transaction history table, cutting read query time from 1.2s to 150ms.

Update:
⚡ **Snappy History: 8x Faster Transaction Loads**
Review your past payments without the wait, thanks to a deep database indexing overhaul that slashes load times to milliseconds.
*Tag: Performance | Backend*

### Now do this one:
Raw feature: We added support for local file encryption using AES-256 for all files uploaded to the MyDrive dashboard so it's safer.
Update:
```

**Why it works:** Writing instructions like *"Be punchy, use an emoji at the start, use bolding for the title, keep the body to one sentence, and put a tag at the bottom"* often yields mixed results. By feeding the model concrete "shots," it instantly mirrors the exact cadence, formatting, and marketing-to-technical balance you want.

---

### Key Takeaway

* **Zero-Shot:** You give a direct command (*"Translate this to French: Apple"*).
* **Few-Shot:** You provide examples first (*"Dog -> Chien, Cat -> Chat, Apple -> "*).

It is one of the easiest ways to radically improve the reliability and structural quality of an LLM's response without touching a single line of training code.

---

## #9 RAG (Retrieval Augmented Generation)

Retrieval - Retrieve the context  

Augmented - Augment the query  

Generation - Generate the response  

---

## #10 Vector DB

You get the context (for LLM) from the data that exists inside your system.  
This data is stored into Vector DB, for example company policy documents, terms and conditions, HR policies etc.

A specialized database optimized for saving document embeddings and performing  
fast semantic similarity searches to provide the right context files for RAG workflows.

---

## #11 MCP (Model Context Protocol)

What if the context exists outside your system?  

As the name suggests, it is a protocol or a way to communicate.  
To transfer context into a model.  

An open communication protocol that serves as a standard wrapper allowing an LLM client  
to fetch real-time data from external servers or databases securely and execute operations.

---

## #12 Context Engineering

Context Engineering is an encapsulation of:  
* Few-Shot Prompting OR Example in Prompt
* RAG (Retrieval Augmented Generation)
* MCP (Model Context Protocol)

Two new challenges in this:  
1. User Preferences
2. Context Summarization

Context Summarization  
For summarization, you might use sliding window algorithm.  
Where the last 10 chats are sent directly to the LLM and  
all the previous chats are summarized.  
This limits the max amount of chats that you are sending directly to the LLM.  

**Context Engineering Vs Prompt Engineering**  

Prompt Engineering is stateless.  
It contains one single prompt.  
No memory required.  

Context Engineering is stateful, it requires memory.  
It evolves as per (1) User Preferences & (2) Context (previous chat history).  

---

## #13 Agents

---

## #14 Reinforcement Learning

It is a way in which you can train models to behave in a particular way.  

Human feedback helps you reinforce good output.  

---

## #15 Chain of Thoughts

LLM goes through a series of deductions or inferences  
and comes up with the final response.

The quality of this response is usually much higher than a direct response.  

LLM breaks the problem (input) into multiple steps.  
If the problem is hard then it may have more steps,  
and if the problem is easy then it may have less steps.  
