r/ChatGPT
4 mo. ago
by 
Zaki_1052_
Join

Efficient Prompt for Note-Taking
You are NotesGPT, an AI language model skilled at taking detailed, concise, and easy-to-understand notes on various subjects in bullet-point format. When provided with a passage or a topic, your task is to:

Create advanced bullet-point notes summarizing the important parts of the reading or topic.

Include all essential information, such as vocabulary terms and key concepts, which should be bolded with asterisks.

Remove any extraneous language, focusing only on the critical aspects of the passage or topic.

Strictly base your notes on the provided information, without adding any external information.

Conclude your notes with [End of Notes] to indicate completion.

By following this prompt, you will help me better understand the material and prepare for any relevant exams or assessments. The subject for this set of notes is: “___”. The following are the headings/sections to focus on:

This one has been super useful for school; I basically never have to read my textbook any more!

When using GPT-4, I use this for #5:

 5. Conclude your notes with [End of Notes, Message #X] to indicate completion, where "X" represents the total number of messages that I have sent. In other words, include a message counter where you start with #1 and add 1 to the message counter every time I send a message.
For when it starts to run out of tokens, or just every long section to remind it, I use:

Please continue taking notes in the established format. Remember to:
1. Create concise, easy-to-understand advanced bullet-point notes.
2. Include essential information, bolding (with **asterisks**) vocabulary terms and key concepts.
3. Remove extraneous language, focusing on critical aspects.
4. Base your notes strictly on the provided passages.
5. Conclude with [End of Notes, Message #X] to indicate completion, where "X" represents the total number of messages that I have sent (message counter).
Your notes will help me better understand the material and prepare for the [Placeholder] exam. 
We will continue with our current topic.
---
Hope these help!


Upvote
106

Downvote

21
comments

Share
Share
Sort by:

Best
Log in to sort by top, controversial, or new
21 comments

Add a Comment
u/AutoModerator avatar
AutoModerator
•
 Stickied comment
•
4 mo. ago
Moderator Announcement Read More »

Upvote
1

Downvote

Reply
reply

Share
Share

PurpleVermont
•
4 mo. ago
Interesting. Have you checked whether it is adding external information or not? And whether it is adding any "hallucinated/confabulated" content? I would guess that the instruction to include only information from the input and nothing else might not be something a language model today could do very well.



Upvote
13

Downvote

Reply
reply

Share
Share

Zaki_1052_
•
4 mo. ago
I did notice when I hadn't added that point it would go off and hallucinated things that weren't in the text, but once I told it to stick to the input, it would be pretty exact and only truncate the passages.

At the beginning, I cross-referenced constantly and it was completely accurate with GPT-4 as far as I could tell, but 3.5 does occasionally make that mistake, yes.


Upvote
4

Downvote

Reply
reply

Share
Share

klippo55
•
4 mo. ago
very useful, i suggest to add text température for better results



Upvote
5

Downvote

Reply
reply

Share
Share

jmonman7
•
4 mo. ago
How do you do that? I’ve seen it before but have been looking for how to use it with ChatGPT


Upvote
2

Downvote

Reply
reply

Share
Share


2 more replies
jmonman7
•
4 mo. ago
I honestly like the output of my notetaking prompts better! The first looks similar to yours except much shorter: "The following is a portion of a transcript that I would like broken down as if it is to be on a PPT, but do not mention "slides , etc.".. Include as much information as possible using bullet point format - please organize as well. Include examples and explanations included in the text:"

Then my following prompt cleans it up and organizes it in PPT style:" Please organize and provide more information on the previous notes using headings and subheadings using bullet points - do not have an intro or conclusion as it is part of a growing list of notes — needs a lot of detail. Do not mention "speaker." Please incorporate examples given within the notes (i.e., do not create a separate section for it)."

if more information is needed, i specify the sections that need more info from the text. then once I've assembled many notes, I clean it all up with GPT-4:

Please help me organize the following "Notes to be Reorganized" by using a bullet point format, indenting subpoints, and breaking down information into concise phrases. Do not remove any essential information i.e., add as much nuance on all areas from the source without extrapolating beyond the source. Do not remove any examples as they are helpful when add additional context. Use the following notes as an example: Example:

Meeting Notes:

Notes were provided for attendees Access to the meeting agenda was offered.

Clarification of issues was also offered

Paper list was to be sent out to keep track of:

Test requests

Budget changes

Overages and Billings:

Overages and billings were discussed

Specifically regarding SLPs over 55 and those who have been assigned to cover overages.

It was advised to have a conversation with the assigned SLP regarding:

Coverage

Billing

A directive from management regarding billing was mentioned

As well as a link to access flip-ups.

Also discussed:

Building time for SLPs

Accommodating their schedules

Collaboration among team members and productive outcomes were encouraged.

Notes to be reorganized:"

That prompt cleans it all up quite nice. I really like the "bolding (with asterisks) vocabulary terms and key concepts" addition though. Also, didn't mean to take away from your post; just an alternative.



Upvote
3

Downvote

Reply
reply

Share
Share

Zaki_1052_
•
4 mo. ago
All good; yours seems pretty effective as well! Different use cases, though; I want it to truncate my textbooks for studying purposes, but I can see how yours is really good for work.

I've found that asking for specifics like that takes away from the simplicity of the content. Especially since classes usually focus on concepts and the like that you'd get from reading long passages, I like to have conversations where I can just scroll down and read as if they're my materials. I have something similar though for when I want explanations for things focused on learning theory, as opposed to esoteric information collating.


Upvote
3

Downvote

Reply
reply

Share
Share

parnex
•
2 mo. ago
Thanks for the prompt <3


Upvote
2

Downvote

Reply
reply

Share
Share

Polargeist
•
15 days ago
Thanks for this amazing prompt! Been using these on Youtube videos & they're better than the one I created.



Upvote
2

Downvote

Reply
reply

Share
Share

Zaki_1052_
•
15 days ago
Glad you like it!

Edit: Thanks for the award!


Upvote
2

Downvote

Reply
reply

Share
Share

Famous_Leather_8134
•
4 mo. ago
Is there a way to get around the text limit?



Upvote
1

Downvote

Reply
reply

Share
Share

Zaki_1052_
•
4 mo. ago
Which one do you mean, like the context window? You can use the shorter prompt at the bottom, but I usually just break the source passages into sections, since the notes are more comprehensive that way. If you mean the output limit, just tell it to "continue" or use the API.


Upvote
1

Downvote

Reply
reply

Share
Share


3 more replies
u/Iammeimei avatar
Iammeimei
•
4 mo. ago
Dumb question:

Do you just copy and paste directly from a pdf of the textbook?



Upvote
1

Downvote

Reply
reply

Share
Share

Zaki_1052_
•
4 mo. ago
Not dumb; a lot of people build tools on LangChain to automatically extract text and the like, but that's a bit beyond me at the moment! I do intend to see what it can build me from my limited experience eventually, it just hasn't been a priority.

My school uses online textbooks, so I just copy and paste directly, and the same for PDFs, yes. And for the few that require physical, I use text detection and GPT-4 will understand what it means through any formatting errors.

If you have any coding experience, I'd recommend getting GPT to build you a tool, or a plugin if you have them yet, that can import PDFs and extract image text directly. Otherwise copy-and-pasting from larger corpuses can be a a bit of a chore.



