---
layout: post
title: "🚀 Building My Blog with ChatGPT"
date: 2025-03-22
categories: [tech, blogging, jekyll]
tags: [jekyll, github-pages, so-simple-theme, chatgpt, blogging]
excerpt: How I used ChatGPT to launch a Jekyll blog with GitHub Pages and the So Simple theme.
author: Tom Gillam
image: assets/images/2025-03-22-hero.jpg
---
Perplexity wrote this blog post (to avoid conflicts of interest when criticizing ChatGPT). I edited this blog post.

---
## **Key Takeaways**
These are the big takeaways from my perspective when writing this post. My takeaways are subject to change.

1. **ChatGPT Excels at Granular Tasks**  
   When asked specific questions (e.g., "How do I override a Jekyll layout?"), ChatGPT provided clear, actionable steps.

2. **High-Level Guidance Leads to Better Results**  
   By asking for broader guidance first (e.g., "How do I set up a blog with this theme?"), I could refine my queries to get more targeted help later.

3. **Role-Playing Enhances Context**  
   Assigning ChatGPT a role (e.g., “You are my coding assistant”) helped it tailor responses more effectively. Additionally, providing context through conversation improved its suggestions.

4. **AI Has Limits**  
   While ChatGPT was immensely helpful, its lack of full project context occasionally led to overly complex or incomplete solutions. Combining its advice with careful testing and documentation review was essential.


### Building a Blog Site with GitHub Pages Using the So Simple Jekyll Theme

I built this site using the So Simple Jekyll Theme, guided by ChatGPT, and hosted on GitHub pages. I have never built a Jekyll site before and I thought it would be easier with ChatGPT.

---

### **What is GPT?**
GPT (Generative Pre-trained Transformer) is an advanced AI model designed to generate human-like text, assist with problem-solving, and provide creative or technical guidance.

---

### **The Process**

Here’s how I built my blog site:

1. **Cloning the Theme**  
   ChatGPT suggested starting by cloning the So Simple Jekyll theme repository. This theme is minimalistic and highly customizable, making it perfect for a clean blog design. The steps included:
   - Adding the theme to my GitHub repository using the `remote_theme` method in `_config.yml`.
   - Running `bundle install` locally to set up dependencies.

2. **Customizing the Blog**  
   Based on ChatGPT’s recommendations, I modified various aspects of the theme:
   - Updated `_config.yml` to reflect my blog's title, description, and preferred settings.
   - Customized layouts and styles by overriding specific files (e.g., `_includes` and `_layouts`).
   - Tweaked colors and fonts in `assets/css/main.scss`.

3. **Debugging Issues**  
   Debugging was not fun. Some of ChatGPT’s suggestions worked seamlessly, while others required adjustments due to missing context or overly detailed solutions that introduced new challenges. For example:
   - Fixing broken links caused by incorrect paths in `_config.yml`.
   - Resolving layout conflicts by carefully reviewing theme documentation.

---

### **Challenges with ChatGPT**

- **Contextual Gaps**: Without full visibility into my project files, ChatGPT sometimes made incorrect assumptions.
- **Overly Detailed Solutions**: At times, its responses were too intricate for simple problems, leading to unnecessary complications.

---

### **Recommendations for Working with GPT Models**

1. **Start Broad, Then Go Deep**: Begin with high-level questions before diving into specifics.
2. **Provide Context**: Share relevant details about your project to improve response accuracy.
3. **Test Incrementally**: Implement changes step-by-step to catch errors early.
4. **Use Documentation**: Supplement AI guidance with official documentation for themes or tools you’re using.
5. **Engage in Dialogue**: Treat interactions as a conversation—clarify responses and iterate on solutions.

---

### **Conclusion**

Building this blog showcased the strengths and limitations of AI tools like ChatGPT. The trick was leveraging ChatGPT's granular expertise while maintaining oversight of the bigger picture because ChatGPT doesn't replace your skills.

Citations:
[1] https://github.com/mmistakes/so-simple-theme
[2] https://www.sugarscape.net/blog/customize-jekyll-so-simple-theme-category-name/
[3] https://davidlozzi.com/2023/10/20/__trashed/
[4] https://mademistakes.com/work/jekyll-themes/so-simple/
[5] https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/adding-a-theme-to-your-github-pages-site-using-jekyll
[6] https://jekyllrb.com/docs/themes/
[7] https://docs.github.com/en/pages/quickstart
[8] https://stackoverflow.com/questions/74721967/how-to-install-this-jekyll-theme-correctly-in-order-to-make-custom-adjustments
