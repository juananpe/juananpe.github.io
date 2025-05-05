# Hugo Content Management Instructions

## Image Handling in Hugo Content

When adding content (like a blog post or page) to this Hugo project that includes images:

1. **Store Images Correctly:**
   - Place all images in the `/opt/hugo/static/images/` directory
   - If the `static/images/` directory doesn't exist, create it first
   - When moving external images (from `/tmp`, absolute paths, or web URLs), copy them to this directory

2. **Reference Images in Content Pages:**
   - For posts and pages, use the `figure` shortcode with the correct path:
     ```markdown
     {{< figure src="/images/your-image.png" alt="Your Alt Text" >}}
     ```
   - Note: Use a leading forward slash `/` to make the path absolute from the site root
   - This approach works consistently regardless of:
     - Page location (posts, archives, or other sections)
     - Base URL configuration
     - Whether the site is served locally or deployed

3. **Reference Images in Templates:**
   - In templates, use `absURL` for image paths:
     ```html
     <img src="{{ "images/your-image.png" | absURL }}" alt="Your Alt Text">
     ```
   - This ensures proper URL generation regardless of base URL configuration

## Post Management and Archives

1. **Content Structure:**
   ```
   content/
     ├── posts/           # All blog posts go here
     │   ├── post1.md
     │   ├── post2.md
     │   └── post3.md
     ├── archives.md      # Archives page
     └── about.md         # About page
   ```

2. **Adding New Posts:**
   - Place all new posts in the `content/posts/` directory
   - Posts will automatically appear on the homepage if they're among the most recent
   - The number of recent posts shown on homepage is controlled by `recent_posts_number` in `config.toml` (default: 3)
   - Older posts automatically move to the archives page

3. **Archives System:**
   - The archives page shows all posts except the most recent ones
   - Posts are displayed in reverse chronological order
   - Pagination is enabled (12 posts per page)
   - The archives use the same card-style layout as the homepage
   - No manual intervention needed - Hugo handles the transition automatically based on post dates

4. **Post Front Matter:**
   ```yaml
   ---
   title: "Your Post Title"
   date: YYYY-MM-DD
   draft: false
   tags: ["tag1", "tag2"]
   ---
   ```

## Link Handling in Hugo

1. **Internal Links in Templates:**
   - Use `relURL` for internal links:
     ```html
     <a href="{{ "your-page" | relURL }}">Link Text</a>
     ```
   - Don't include leading or trailing slashes in the path
   - Hugo will automatically handle the base URL prefix

2. **External Links:**
   - Use complete URLs for external links:
     ```markdown
     [Link Text](https://external-site.com/path)
     ```

## Best Practices for GitHub Pages Deployment

1. **Configuration:**
   - In `config.toml`, set your `baseURL` to match your GitHub Pages URL:
     ```toml
     baseURL = "https://username.github.io/repository-name/"
     ```

2. **Local Testing:**
   - Test with the same base URL structure:
     ```bash
     hugo server --baseURL "http://localhost:1313/repository-name/" --appendPort=false
     ```

3. **URL Structure:**
   - Never hardcode the repository name (e.g., "genai-crew") in paths
   - Use Hugo's built-in URL handling functions (`relURL`, `absURL`)
   - Let Hugo handle all URL generation based on the `baseURL` setting

4. **Troubleshooting:**
   - If images/links work locally but not on GitHub Pages, check:
     - Path cases (GitHub Pages is case-sensitive)
     - Leading/trailing slashes
     - Use of relative vs. absolute paths
   - Use browser developer tools to check actual URL paths

Remember: These practices ensure your site works consistently both locally and when deployed to GitHub Pages, and remains maintainable if the base URL changes.

## Homepage Highlighting Process for New Posts

When a new post is added and you want to update the homepage highlights:

1. **Highlight the new post as the first (leftmost) box** in the main section.
2. **Move the previous third (rightmost/oldest) box** from the main section to the "Previously Covered" section, appending it after any existing entries there.
3. The "Previously Covered" section should accumulate all older posts, in the order they were moved out of the main section.

This ensures the AI Agent Protocols Survey remains a permanent highlight, and the homepage always features the latest content and a consistent historical record. 