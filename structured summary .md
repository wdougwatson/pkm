
Both prompts should be added before after the text that needs to be summarized.

Structured summary:

( end of TEXT )

TASK: TL;DR/SUMMARY of TEXT in JSON. JSON keys: "titles" (array of strings): 2-5 appropriate titles for TEXT; "tags" (string): tag cloud; "entities" (array of {"name", "description"} objects): named entities, including persons, organizations, processes, etc. their detailed description and relationships; "short_summaries" (array of strings): one-two sentence summaries of TEXT; "style" (string): type, sentiment and writing style of TEXT; "arguments" (array of strings): 5-10 main arguments of TEXT; "summary" (string): detailed summary of TEXT

Incremental summary:

( end of TEXT )

Summarize TEXT by producing a series of summaries, starting with a one-sentence summary and then creating subsequent summaries that are each about twice as long as their predecessor. It is essential that each summary is a complete and thorough representation of TEXT, independent of the other summaries, so that the reader can understand the content without needing to refer to any of the other summaries for context or clarification. Create a total of 3-5 independent summaries of progressively increasing size.

The second prompt only works with GPT-4.