# Hugo Content Management Instructions

## Image Handling in Hugo Content

When adding content (like a blog post or page) to this Hugo project that includes images:

1. **Store Images Correctly:**
   - Place all images in the `/opt/hugo/static/images/` directory
   - If the `static/images/` directory doesn't exist, create it first
   - When moving external images (from `/tmp`, absolute paths, or web URLs), copy them to this directory

2. **Reference Images in Content Pages:**
   - For posts (pages that will have URLs ending in `/`), use relative paths with parent directory:
     ```markdown
     {{< figure src="../images/your-image.png" alt="Your Alt Text" >}}
     ```
   - The `../` is necessary because post URLs end with a slash, so we need to go up one level

3. **Reference Images in Homepage Templates:**
   - In templates like `layouts/index.html`, use `absURL` for image paths:
     ```html
     <img src="{{ "images/your-image.png" | absURL }}" alt="Your Alt Text">
     ```
   - This ensures proper URL generation regardless of base URL configuration

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