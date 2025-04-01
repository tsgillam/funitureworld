---
layout: post
title: "Robot Blog"
date: 2025-04-01
author: "Tom Gillam"
categories: [blog, chatgpt, prompt engineering, prompt flow]
tags: [chatgpt, prompt engineering, blog]
excerpt: "I quickly build a blog that uses a python file to generate blog posts from ChatGPT."
---

# Key Points
I wanted to get a robot blog up and running with minimal effort. Here’s a behind-the-scenes look at how this robot blog came to life, what worked, what didn’t, and what's next.

1. Keeping things simple is worth the extra effort.
2. ChatGPT tends to over complicate.

# Create the blog
1. I created the blog using this [quickstart guide](https://docs.github.com/en/pages/quickstart).
2. ChatGPT generated the [readme.md](https://chatgpt.com/?prompt=Write%20a%20basic%20readme.md%20file%20for%20a%20fake%20blog%20with%20posts%20generated%20by%20Chatgpt) file - this is basically the homepage.
3. Chat GPT also generated the [index.md](https://github.com/tsgillam/robot-blog/blob/main/index.md) file that lists the posts.
4. I added a [_posts](https://github.com/tsgillam/robot-blog/tree/main/_posts) folder for the post .md files jekyll uses.

# [Create a system prompt](https://chatgpt.com/?prompt=Write%20a%20system%20prompt%20template%20that%20accepts%20a%20persona%20and%20writes%20a%20blog%20post%20on%20a%20topic)
The initial plan was to use a system prompt and a user prompt. I started with the system prompt.

```yaml
system_prompt: |
  You are a content strategist and expert copywriter, generating a blog post tailored to a specific persona. The writing must reflect the persona’s tone, values, and communication style while offering informative, engaging, and well-structured content on the given topic.

  ---  
  🎭 Persona Details:
  - Name: {persona_name}
  - Role/Profession: {persona_role}
  - Interests: {persona_interests}
  - Writing Tone: {persona_tone}
  - Content Goals: {persona_goals}
  - Target Audience: {persona_audience}
  - Additional Style Notes: {persona_style_notes}

  📝 Blog Post Topic:  
  {blog_topic}

  🎯 Instructions:
  1. Write a blog post that aligns with the persona’s tone and goals.
  2. Start with a hook or intro that grabs attention.
  3. Structure the content with headings, clear flow, and thoughtful transitions.
  4. Use specific examples, analogies, or data where helpful.
  5. Conclude with a takeaway or call-to-action relevant to the audience.
  6. Format for readability (short paragraphs, lists, etc.).

  Only write the blog post — do not explain or summarize your process.
```

# [Generate personas using the template](https://chatgpt.com/prompt=generate%20personas%20for%20a%20cave%20man%2C%2090%27s%20rapper%2C%20pirate%2C%20and%20robot%20using%20the%20yaml%20template%20suggeste)

```yaml
persona_name: Captain Redbeard Blackboot
persona_role: Swashbuckling Buccaneer and Treasure Hoarder
persona_interests: Sailing, gold doubloons, parrots, rum, mutiny
persona_tone: Boisterous, nautical, with classic pirate lingo
persona_goals: Recruit new deckhands, share tales of the sea, boast about plunder
persona_audience: Landlubbers, fellow pirates, nautical bloggers
persona_style_notes: Start with “Ahoy!”, toss in “Arrr”, “ye”, and “me hearties” liberally
blog_topic: Top 5 Hidden Coves for Buryin’ Yer Treasure Without the Navy Catchin’ Wind
```

# [Create a user prompt](https://chatgpt.com/prompt=Write%20a%20user%20prompt%20that%20would%20auto-generate%20a%20blog%20post%20using%20this%20system%20prompt)
After experimenting with pirate slang and rapper personas, I realized the ChatGPT personas were painful. Here is the final persona file.

```yaml
ben_bernanke:
  persona_name: Ben Bernanke

jerome_powell:
  persona_name: Jerome Powell

janet_yellen:
  persona_name: Janet Yellen
```

The user prompt can include a persona, so I don't need a separate system prompt.

```yaml
user_prompt: |
I want you to write a blog post using the persona and topic details I’ve provided below.
Make sure the content reflects the persona’s unique tone, style, and goals while being engaging and informative. Use the persona’s characteristics to shape the writing, including vocabulary, references, and phrasing.
Keep the blog post simple and short.

  **Persona Details:**
  - Persona Name: {persona_name}

  **Blog Topic:**
  {blog_topic}

  Please write the blog post now, following the system’s instructions.
```

# [Write the python script](https://chatgpt.com/?prompt=Write%20a%20python%20script%20to%20read%20the%20user_prompt.yml%20file%20and%20the%20personas.yml%20file%20and%20create%20the%20user%20prompt%20to%20generate%20a%20blog%20post%20using%20the%20template%20and%20a%20random%20persona) ###

```python
import yaml
import random
from jinja2 import Template

# Load the user prompt template
def load_template(path='user_prompt.yml'):
    with open(path, 'r') as f:
        data = yaml.safe_load(f)
    return data['user_prompt']

# Load personas from YAML file
def load_personas(path='personas.yml'):
    with open(path, 'r') as f:
        return yaml.safe_load(f)

# Fill the prompt template with persona data
def generate_prompt(template_str, persona):
    template = Template(template_str)
    return template.render(**persona)

# Main function
def main():
    template_str = load_template()
    personas = load_personas()

    # Choose a random persona
    persona = random.choice(personas)

    # Generate the user prompt
    prompt = generate_prompt(template_str, persona)

    print("🎯 Generated User Prompt:\n")
    print(prompt)

if __name__ == "__main__":
    main()
```

# [The robot blog](https://tsgillam.github.io/robot-blog/)

**Why Nvidia’s Stock Is More Than Just Hype**  
*By Ben Bernanke*

If you're wondering why Nvidia’s name keeps popping up in financial headlines, you're not alone — and you're not wrong to pay attention. While I spent years focused on monetary policy and macroeconomics, one thing I learned is this: when technology shifts, markets follow.

Nvidia’s rise isn’t just about gaming graphics anymore. It’s about **AI**, **data centers**, and the infrastructure behind the digital economy. In many ways, Nvidia is becoming what railroads were to the 19th century — the tracks everything else runs on.

Its stock performance? Impressive, yes — but also reflecting genuine demand for its chips in powering everything from ChatGPT to self-driving cars. Is it priced for perfection? Possibly. But in a world increasingly driven by computation, it's a name worth watching.

Sometimes, markets do get excited. But sometimes, they’re just early to the truth. Nvidia might be both.

— Ben

# What's next
1. Debugging the jekyll site.
2. Use ChatGPT to automate blog post editing.
