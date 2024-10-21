**Code example - Appendix A: GPT4 API Code Snippet w/ response in a json format**

```python
from openai import OpenAI

client = OpenAI(
            api_key="insert_your_api_key_here",
        )

prompt_llm = """You are a customer support agent reading through customer provided free text comments as to why they did not show up to their appointment. 
You'll be provided a list of 100 comments separated by a semi-colon as the delimiter. For example, the following are 3 different comments separated by "; "
"Work overtime; I had it down on my schedule as Monday instead of Sunday ; Family emergency ;"

You will extract the most common themes of the comments and respond in json format, with the theme as the key and 3 example comments exemplifying the theme in a list.
For example, you could respond as
{'work conflict': ['I had to work', 'I work nights', 'I forgot I worked early today'],
'personal conflict': [''Had a family matter come up, apologies.', ''My mom was sick. She has stage 4 lung cancer. I was helping her.', 'I had to run my son to the hospital']}
"""

prompt = "insert your message / what you want the LLM to answer"

chat_completion = client.chat.completions.create(
                messages=[
                    {
                        "role": "system",
                        "content": prompt_llm,
                    },
                    {
                        "role": "user",
                        "content": prompt,
                    }
                ],
                model="gpt-4-1106-preview",
                response_format = {"type": "json_object"}
            )


json_answer = json.loads(chat_completion.choices[0].message.content)

```
