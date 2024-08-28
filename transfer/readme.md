GitHub handles image storage in Markdown (`.md`) files by either embedding images directly from a URL or storing the images within the repository itself. Here's how GitHub manages images in Markdown files:

### 1. Embedding Images from a URL

When you include an image in a Markdown file using a URL, GitHub doesn't store the image directly. Instead, it references the image from its external location. Here's how you might embed an image using a URL in Markdown:

```markdown
![Alt text](https://example.com/image.png)
```

- **Alt text**: A description of the image for accessibility purposes.
- **URL**: The direct link to the image hosted on an external server.

In this case, the image is not stored on GitHub's servers. GitHub's Markdown renderer fetches the image from the specified URL each time the Markdown file is viewed.

### 2. Embedding Images from the Repository

You can also store images directly within the GitHub repository. This is often done by placing the image file in a folder within the repository and referencing it in the Markdown file using a relative path. Here's how you can embed an image stored in the repository:

```markdown
![Alt text](./images/my-image.png)
```

- **Relative path**: The path to the image file relative to the location of the Markdown file.

#### Steps for Storing and Displaying Images in a Repository

1. **Add the Image to the Repository**:  
   You can upload images directly to your repository by dragging and dropping them into the file view or using Git commands. The image will be stored as a binary file in the repository.

2. **Reference the Image in the Markdown File**:  
   Use a relative path to reference the image in your Markdown file. This path should point to the location of the image within the repository's file structure.

For example, if your repository structure looks like this:

```
/my-repo
  /images
    - my-image.png
  - README.md
```

You would reference the image in `README.md` like this:

```markdown
![My Image](./images/my-image.png)
```

### How GitHub Handles Stored Images

- **Storage**: Images stored in a GitHub repository count against the repository's total storage quota. GitHub repositories have a storage limit (as of now, it's typically 1 GB per repository for free users, but this limit can vary based on your GitHub plan).
  
- **Version Control**: GitHub's version control system (Git) tracks changes to binary files like images, but this can increase the repository size quickly if images are frequently updated.

- **Rendering**: When a Markdown file with an embedded image is viewed on GitHub, GitHub's servers render the Markdown and fetch the image file from the repository to display it inline with the text.

### Summary

- **External Images**: Referenced via URLs, not stored on GitHub.
- **Internal Images**: Stored within the repository, referenced via relative paths, and count towards repository size.

By understanding these methods, you can manage images in your GitHub Markdown files effectively, balancing storage constraints and convenience.
