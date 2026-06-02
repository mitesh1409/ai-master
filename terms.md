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

**The Architecture of Context**  

When you interact with an AI tool like Cursor, the full "context" sent to the model looks like this:  

* System Prompt: The foundational instructions, rules, and behavioral constraints (the "ground rules").

* User Prompt: The specific question or task you just typed.

* Conversation History / Code Files: The surrounding details (your previous messages, open files, linter errors) that give concrete background.

**System Prompt vs. User Prompt**  

| Feature | System Prompt | User Prompt |
| --- | --- | --- |
| Who Writes It? | The application developers (e.g., Cursor) or you via global settings (`.cursorrules`). | You, dynamically, in the chat box or inline edit block. |
| When is it Applied? | It is injects invisibly at the very beginning of every single session or request. | It changes with every message you send. |
| Purpose | Sets the AI's persona, formatting rules, restrictions, and core coding standards. | Demands a specific, immediate action (e.g., "Fix this bug", "Write a test").|

## Tool Calling

**How tool calling works**  

When developers build AI applications, they can define specific "tools" that the AI model can use. These tools are like special abilities that extend what the model can do beyond just thinking and responding with text.

When you ask ChatGPT to generate an image, search the web, or run code, it's using tools behind the scenes.

AI models can call tools to extend their capabilities.

Here's what happens under the hood:  

1. The AI model receives your request and recognizes it needs additional capabilities
2. It formats a special response in JSON (a structured data format) that specifies which tool to use and what parameters to pass
3. The application runs that tool and returns the results
4. The AI model incorporates those results into its context and continues the conversation

**What's inside a tool call?**  

Every tool has three main components:

1. A name like read_file or search_web  
2. A description that tells the model when and how to use the tool
3. Parameters which are the inputs the tool needs to work

Here's an example of what a tool definition might look like:  

```json
{
  "name": "read_file",
  "description": "Read the contents of a file from the codebase",
  "parameters": {
    "filepath": "The path to the file to read"
  }
}
```

## MCP (Model Context Protocol)

Recently, a new standard called MCP (Model Context Protocol) was created. Think of it as a universal way for AI models to use and integrate tools across applications.

Just like how USB became a standard for connecting devices to computers, MCP aims to be a standard for connecting tools to AI models. This means developers can build tools once and have them work across many different AI apps.

## Agents

At its core, an agent is simply **tools in a loop**.

Think of it like this: instead of you having to tell the AI what to do step by step, you give it a goal and let it figure out the steps itself. It's the difference between giving someone turn-by-turn directions versus just telling them the destination (goal) and letting them use GPS (as a tool).

## Agent Harness

An AI harness (or agent harness) refers to the supporting framework, prompt system, and orchestration surrounding a core language model to help it execute complex tasks.

Cursor is an AI editor with a built-in coding agent. The agent runs inside what's called a "harness," which is made up of three things:

1. Instructions: The system prompt and rules that guide behavior
2. Tools: File editing, codebase search, terminal execution, and more
3. Model: The agent model you pick for the task
