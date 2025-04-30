# Prompt for Handling External Images in Hugo Content

When adding content (like a blog post or page) to this Hugo project that includes images referenced from outside the project structure (e.g., from `/tmp`, an absolute path, or a web URL that needs to be saved locally):

1.  **Identify External Images:** Check all image references (`![alt text](...)`) in the provided content or instructions.
2.  **Move Image to `static/images/`:** If an image source is external, move or copy the image file into the `/opt/hugo/static/images/` directory. If the `static/images/` directory doesn't exist, create it first.
3.  **Update Markdown Reference:** Modify the image reference in the markdown file to use a path relative to the site root, starting with `/images/`. For example, change `![Example](/tmp/example.png)` to `![Example](/images/example.png)`.
4.  **Confirm:** Ensure the final markdown content uses the correct `/images/...` path for all local images. 