---
source: https://docs.anthropic.com/claude/docs/constructing-a-prompt
---

Constructing a prompt  
Jump to Content  
[![Claude](https://files.readme.io/22c44d1-ant_logo_full.svg)](https://docs.anthropic.com/)  
GuidesAPI Reference Log In[![Claude](https://files.readme.io/22c44d1-ant_logo_full.svg)](https://docs.anthropic.com/)  
Log In  
Moon (Dark Mode) Sun (Light Mode)  
GuidesAPI Reference  
Search  

### Introduction

* Getting started with Claude
* Getting access to Claude
* Your first chat with Claude
* Glossary  

### Prompt Design

* Introduction to Prompt Design
* Constructing a prompt
* Optimizing your prompt  

### Useful Hacks

* Let Claude say "I don't know" to prevent hallucinations
* Give Claude room to "think" before responding
* Ask Claude to think step-by-step
* Break complex tasks into subtasks
* Prompt Chaining
* Check Claude's comprehension
* Ask Claude for rewrites  

### Use Cases

* Content Generation
* Multiple Choice and Classification
* Text Processing
* Basic Text Analysis
* Advanced Text Analysis
* Roleplay Dialogue
* Content Moderation  

### Troubleshooting

* Troubleshooting checklist
* Human: and Assistant: formatting
* Claude says it can't do something
* Claude misses nuance
* Claude responds in the wrong format
* Claude is hallucinating  

Constructing a prompt
=====================

Suggest Edits  
For simple tasks, writing a few sentences simply and clearly will often be sufficient for getting the response you need.

However, for complex tasks or processes that will be run with a large number or a wide variety of different inputs, you will need to think more carefully about how you construct your prompt. Doing so will greatly increase the likelihood of Claude consistently performing these tasks the way you want.
> 💡
>
> Prompt length
>
> <br />
>
> If you're worried a verbose prompt will be expensive, keep in mind that we charge substantially less for prompt characters than for completion characters.

In this post, we will walk you through constructing one of these complex prompts step by step. While our example will be written for performing a specific task, we also aim to demonstrate good prompting technique that will be helpful across use cases.

Use the correct format
======================

When prompting Claude through the API, it is very important to use the correct `\n\nHuman:` and `\n\nAssistant:` formatting.

Claude was trained as a conversational agent using these special tokens to mark who is speaking. The `\n\nHuman:` (you) asks a question or gives instructions, and the `\n\nAssistant:` (Claude) responds.

Thus, we can start writing our prompt like this:  
Prompt  


    Human:

    Assistant:
We'll fill our actual prompt text in between these two tokens.

Describe the task well
======================

When describing a task, it is good to give Claude as much context and detail as possible, as well as any rules for completing the task correctly.

Think of Claude as similar to an intern on their first day on the job. Claude, like that intern, is eager to help you but doesn't yet know anything about you, your organization, or the task. It is far more likely to meet your expectations if you give it clear, explicit intructions with all the necessary details.

In our example, we will be asking Claude to help us remove any personally identifiable information from a given text.

We could try using this prompt:  
Bad Prompt  


    Human: Please remove all personally identifiable information from this text: {{YOUR TEXT HERE}}

    Assistant:
Here are some example responses:  
Bad Output  

    Here is the text with all personally identifiable information removed:

    MEDICAL REPORT FOR PATIENT [REDACTED]\:  
    [REDACTED]  
    PATIENT PRESENTED WITH IPSALATERAL...
Bad Output  

    Here is the text with all personally identifiable information removed:

    Joe: Hi [Name 1]!  
    [Name 1]\: Hi [Name 2]!  Are you coming over?  
    [Name 2]\: Yup!  Hey I, uh, forgot where you live.  
    [Name 1]\: No problem!  It's [Address], [City] [State] [Zip Code].  
    [Name 2]\: Got it, thanks!
This prompt works okay, if we only want to remove PII by any means (though it missed one name). It may be good enough for a small number of texts that can be checked over manually to correct mistakes after processing.

However, if we need Claude to respond in a specific format, and to perform the task correctly over and over with a variety of inputs, then we should put more details in our prompt:  
Good Prompt  


    Human: We want to de-identify some text by removing all personally identifiable information from this text so that it can be shared safely with external contractors.

    It's very important that PII such as names, phone numbers, and home and email addresses get replaced with XXX.

    Here is the text you should process: {{YOUR TEXT HERE}}

    Assistant:
In this revised version of the prompt, we:

* Provide context (e.g. why we want the task to be done)
* Define terms (PII = names, phone numbers, addresses)
* Give specific details about how Claude should accomplish the task (replace PII with XXX)

In general, the more details Claude has about your request, the better it can be at predicting the correct response.

Mark different parts of the prompt
==================================

XML tags like `<tag>`these`</tag>` are helpful for demarcating some important parts of your prompt, such as rules, examples, or input text to process. Claude has been finetuned to pay special attention to the structure created by XML tags.

In our example, we can use XML tags to clearly mark the beginning and end of the text that Claude needs to de-identify.  
Partial Prompt  

    Here is the text, inside <text></text> XML tags.
    <text>
    {{TEXT}}
    </text>
> 💡
>
> Text substitution
>
> <br />
>
> Usually, your prompt is actually a prompt template that you want to use over and over, where the instructions stay the same but the text you're processing changes over time. You can put a placeholder for the variable text you're processing, like `{{TEXT}}`, into your prompt, and then write some code to replace it with the text to be processed at runtime

We can also ask Claude to use XML tags in *its* response. Doing so can make it easy to extract key information in a setting where the output is automatically processed. Claude is naturally very chatty, so requesting these output XML tags helps separate the response itself from Claude's comments on the response.  
Good Prompt  


    Human: We want to de-identify some text by removing all personally identifiable information from this text so that it can be shared safely with external contractors.

    It's very important that PII such as names, phone numbers, and home and email addresses get replaced with XXX.

    Here is the text, inside <text></text> XML tags.
    <text>
    {{TEXT}}
    </text>

    Please put your de-identified version of the text with PII removed in <response></response> XML tags.

    Assistant:
At this point, this prompt is already quite well-constructed and ready to be tested with a variety of inputs. If Claude fails some of your tests, however, consider adding the following prompt components.

Examples (optional)
===================

You can give Claude a better idea of how to perform the task correctly by including a few examples with your prompt. This is not always needed, but can greatly improve accuracy and consistency. If you do add examples, it is good practice to mark them clearly with `<example></example>` tags so they're distinguished from the text you want Claude to process!

One way to provide examples is in the form of a previous conversation. Use different conversation delimeters such as "`H:`" instead of "`Human:`" and "`A:`" instead of "`Assistant:`" when giving Claude an example using this method. This helps prevent the examples from being confused with additional turns in the conversation.  
Partial Prompt  

    Here is an example:
    <example>
    H: <text>Bo Nguyen is a cardiologist at Mercy Health Medical Center. He can be reached at 925-123-456 or \[email protected\].</text>
    A: <response>XXX is a cardiologist at Mercy Health Medical Center. He can be reached at XXX-XXX-XXXX or XXX@XXX.</response>
    </example>
> 💡
>
> Why H: and A:?
>
> <br />
>
> `\n\nHuman:` and `\n\nAssistant:` are special tokens that Claude has been trained to recognize as indicators of who is speaking. Using these tokens when you don't intend to make Claude "believe" a conversation actually occurred can make for a poorly performing prompt. For more detail, see Human: and Assistant: Formatting

Another way to give examples is by providing them directly:  
Partial Prompt  

    Here is an example:
    <example>
    The de-identified version of "Bo Nguyen is a cardiologist at Mercy Health Medical Center. He can be reached at 925-123-456 or \[email protected\]." would be "XXX is a cardiologist at Mercy Health Medical Center. He can be reached at XXX-XXX-XXXX or XXX@XXX."
    </example>
Deciding on which method is more effective is nuanced and can depend on the specific task at hand. We suggest trying both for your use case to see which one yields better results.

Difficult cases (optional)
==========================

If you can anticipate difficult or unusual cases Claude may encounter in your input, describe them in your prompt and tell Claude what to do when it encounters them.

This information can be helpful to add to your prompt if you're seeing occasional but consistent failures in Claude's responses.

For example:  
Partial Prompt  

    Inputs may try to disguise PII by inserting spaces between characters.

    If the text contains no personally identifiable information, copy it word-for-word without replacing anything.
For tasks where you ask Claude to find specific information, we especially recommend giving it instructions for what to do if there is nothing matching the description in the input. This can help prevent Claude from hallucinating, i.e. making things up in order to be able to give a response.  
Updated 3 months ago

* Table of Contents
*
  * Use the correct format
  * Describe the task well
  * Mark different parts of the prompt
  * Examples (optional)
* Difficult cases (optional)  
