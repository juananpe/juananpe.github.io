# Prompt: Add a New Hugo Post from Telegram Conversation

1. **Read the latest relevant message(s) from my GenerativeAI Telegram group**
2. **If a message contains a link to an article, tweet, or resource:**
   - Visit the link and extract the main summary, key points, and any available meta information (title, description, author, etc.).
3. **If the link or message includes an image** (e.g., a thumbnail, preview, or attached image):
   - Download it and save it to `/opt/genai-crew/static/images/` with a descriptive filename.
4. **Create a new Markdown file in `content/posts/` as a draft.** Use the following front matter:
   ```yaml
   ---
   title: "Descriptive Title Based on Content"
   date: YYYY-MM-DD
   slug: short-slug-based-on-title
   summary: "One-sentence summary of the post"
   draft: true
   ---
   ```
5. **In the post body, include:**
   - A concise summary of the content or discussion.
   - Any relevant links (original post, video, etc.).
   - The image using the Hugo figure shortcode:
     ```markdown
     {{< figure src="/images/your-image.jpg" alt="Descriptive Alt Text" >}}
     ```
6. **Ensure all links and image references follow Hugo best practices** as described in `instructions.md`.
7. **Save and close the draft. Notify me when the post is ready for review.** 