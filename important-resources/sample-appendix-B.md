**Code example - Appendix B: GPT4 API Code Snippet w/ Assistants + PDF upload**

```python
## this code snippet was specific to uploading a resume pdf and extracting information related to the candidate
## use this as a quickstart to understand how to call on the OpenAI API and refine for your purposes

client = OpenAI(
    api_key="insert-your-api-key-here",
)
modeltype = 'gpt-3.5-turbo' #replace w. whatever model type you prefer
fname = 'filename_and_location_relative_to_code'

# name of your assistant
assistant_name = "Resumes Assistant"

# instructions for your "assistant"
# you will need to design this for your use case
instructions =
"""
You are an expert HR analyst that answers questions about a specific resume and candidate.
"""

# content or the "message" you as the user would give to the assistant
# you will need to design this for your use case
content = """
Looking at the top, or first few lines, of this resume, what is the name of the candidate that appears on this resume? 
Answer with only the person's name, no other words. For example, 'Christine Kim Lee'"
"""

# creating an assistant
assistant = client.beta.assistants.create(
  name=assistant_name,
  instructions=instructions,
  model=modeltype,
  tools=[{"type": "file_search"}]
)

# Upload the file indicated by fname to OpenAI
message_file = client.files.create(
  file=open(fname, "rb"), 
    purpose="assistants"
)
# Create a thread and attach the file to the message
thread = client.beta.threads.create(
  messages=[
    {
      "role": "user",
      "content": content,
      # Attach the new file to the message.
      "attachments": [
        { "file_id": message_file.id, 
         "tools": [{"type": "file_search"}] }
      ],
    }
  ]
)
# # The thread now has a vector store with that file in its tool resources.
# print(thread.tool_resources.file_search)

# now run and get GPT's answer to your "message"
run = client.beta.threads.runs.create_and_poll(
thread_id=thread.id, assistant_id=assistant.id)

messages = list(client.beta.threads.messages.list(thread_id=thread.id, run_id=run.id))
message_content = messages[0].content[0].text
# the text returned consists of the annotation/citation so remove it this way
## https://platform.openai.com/docs/assistants/tools/file-search/quickstart?context=without-streaming
annotations = message_content.annotations
citations = []
for index, annotation in enumerate(annotations):
    message_content.value = message_content.value.replace(annotation.text, "").replace(".", "")
    if file_citation := getattr(annotation, "file_citation", None):
        cited_file = client.files.retrieve(file_citation.file_id)
        citations.append(f"[{index}] {cited_file.filename}")

# more stripping of text for "pretty print"
cand_name = message_content.value.replace(".", "").strip()
```
