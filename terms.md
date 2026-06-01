# AI Terms

## AI Models

You can think of them like super intelligent, general purpose API endpoints. Just like you would integrate the Stripe API to handle payments, or Twilio to send text messages, you can call an AI model to solve a variety of tasks.

The biggest difference is: you are not guaranteed to get the same results every time.

## Modalities

You can also interact with models in different ways, or “modalities”. For example, through text into a chatbot, generating an image, talking to a virtual AI, or even generating video from prompts.

For building software, using different modalities might look like:

1. Using text to describe the product or feature you want to build, working with the AI together to define a plan
2. Using images to share mockups or designs for the UI you’re trying to build, or providing feedback back to the AI model if the spacing or colors aren’t right
3. Using voice to transcribe what you’re saying into an input for the AI model, saving you from needing to type out long or detailed instructions

## The Knowledge Cutoff

The latest known knowledge that models have.

The AI Model providers are taking just a ton of text/image/audio/video data or proprietary data on the internet to train these models and it's up to some date called "The Knowledge Cutoff".

## Hallucinations

Hallucination is when an AI model confidently generates information that seems plausible but is actually incorrect. It's like when someone tries to bluff their way through a conversation about a topic they don't really know.

When you ask AI Model something that is beyond its knowledge cutoff date then there are higher chances that it will hallucinate.

plausible = that you can believe; believable, reasonable  
Plausible means an idea, explanation, or statement that seems reasonable, believable, or likely to be true, even if it hasn't been completely proven. It suggests that something makes logical sense and is easy to accept.  

astray = moving off the right path or route, getting lost in transit  
Astray is an adverb or adjective meaning to wander away from the correct, intended, or morally right path. It implies being lost, off-course, or misled.

## Tokens

Tokens are the words that AI Model can actually understand.  

Tokens are not the same as words we use in a language.  

AI Models don't work directly with words like "Hello" or "World" either.  
They break everything down into smaller chunks called tokens.  

[OpenAI Tokenizer](https://platform.openai.com/tokenizer)

AI Models are priced based on token usage.  
You pay per token, not per word or character.  

TPS (Tokens Per Second)  
Many folks measure the speed of a model in TPS.  
Faster model is gonna generate more TPS.  

Tokens are the units that we can use to measure and charge for the input and output traffic.  

So we are working with two different types of tokens:  
1. **Input Tokens:** includes everything that you send to the model, like your "prompt" and the existing conversation. Input Tokens = User Prompts + Existing Context  
2. **Output Tokens:** what the model generates back to you. Output Tokens = Model Response  

Output Tokens typically cost more than Input Tokens, because generating response (output)  
requires a bit more computational work than just processing what you sent (input).  

## Context

