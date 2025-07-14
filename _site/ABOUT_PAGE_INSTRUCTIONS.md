# About Page Instructions

This guide will help you customize the `_includes/about.html` file for your personal website.

## Overview

The about page is divided into two main sections:
- **Left Section**: Your profile information, bio, and professional links
- **Right Section**: Your recent news and achievements

## How to Fill Out Each Section

### 1. Profile Image
**Location**: Line 12 in `_includes/about.html`

```html
<img src="/assets/img/me/[your-image-filename]" alt="[your name] profile image" />
```

**Instructions**:
- Replace `[your-image-filename]` with your actual image filename (e.g., `profile.jpg`)
- Place your profile image in the `/assets/img/me/` directory
- Update the `alt` text with your name for accessibility

### 2. Name and Tagline
**Location**: Lines 17-20

```html
<h1>[Your Full Name]</h1>
<h3>[Your Role]. [Your Focus]. [Your Passion].</h3>
```

**Instructions**:
- Replace `[Your Full Name]` with your complete name
- Replace the three-part tagline with 3-4 words describing you
- **Examples**:
  - "Builder. Researcher. Explorer."
  - "Developer. Designer. Creator."
  - "Engineer. Innovator. Leader."

### 3. Bio Section
**Location**: Lines 22-48

**Instructions**:
- **Current Status**: Describe what you're currently doing (job, studies, project)
- **Previous Experience**: Mention your most relevant past experience
- **Interests**: Share what you're passionate about
- **Links**: Include relevant organization/company URLs

**Bio Template**:
```html
Currently [your current role/studies] at 
<a href="[organization-url]" target="_blank" style="text-decoration: underline; color: #268bd2">[Organization Name]</a>. 

Previously, [previous role] at 
<a href="[company-url]" target="_blank" style="text-decoration: underline; color: #268bd2">[Company Name]</a>. 

Passionate about [your interests/focus areas].
```

### 4. External Links
**Location**: Lines 32-42

**Instructions**:
- Update the blog link if your blog is external
- Replace `[your-external-blog-url]` with your external blog/platform URL
- Replace `[External Platform Name]` with the platform name (e.g., "Medium", "Substack")
- Add context about what type of content you share there

### 5. CV/Resume Download
**Location**: Lines 52-58

**Instructions**:
- Replace `[Your_CV_Filename].pdf` with your actual CV filename
- Place your CV file in the `/assets/` directory
- Make sure the filename matches exactly

### 6. Professional Profiles
**Location**: Line 61

**Instructions**:
- Replace `[your-credly-url]` with your actual profile URL
- Replace `[Platform Name]` with the platform name (e.g., "Credly", "LinkedIn")
- This section is optional - remove if not needed

### 7. Picture Context (Optional)
**Location**: Lines 63-70

**Instructions**:
- Describe where/when your profile photo was taken
- Add any interesting context about the location
- Link to relevant institutions or locations
- This section is optional - remove if not needed

## Recent News Section

### Adding News Items

Each news item follows this structure:

```html
<div class="news-item">
  <h3><span class="news-date">[Month DD, YYYY]</span></h3>
  <p>
    [Your achievement/news description]
    <a
      target="_blank"
      style="text-decoration: underline; color: #268bd2"
      href="[relevant-url]"
    >
      [Link Text]</a
    >
    [Additional context if needed].
  </p>
</div>
```

### News Item Types & Examples

#### 1. Certifications/Achievements
```html
<div class="news-item">
  <h3><span class="news-date">Jun 14, 2025</span></h3>
  <p>
    Excited to share that I've officially become a 
    <a target="_blank" style="text-decoration: underline; color: #268bd2" href="[certification-url]">
      [Certification Name]</a>
  </p>
</div>
```

#### 2. Program Acceptances
```html
<div class="news-item">
  <h3><span class="news-date">Apr 17, 2025</span></h3>
  <p>
    Grateful to be accepted for the 2025
    <a target="_blank" style="text-decoration: underline; color: #268bd2" href="[program-url]">
      [Program Name]</a>
    in [Location].
  </p>
</div>
```

#### 3. Projects/Publications
```html
<div class="news-item">
  <h3><span class="news-date">Feb 25, 2024</span></h3>
  <p>
    Grateful to have presented our project on
    <a target="_blank" style="text-decoration: underline; color: #268bd2" href="[project-url]">
      [Project Title]</a>
    at [Event/Institution Name].
  </p>
</div>
```

#### 4. Speaking/Workshops
```html
<div class="news-item">
  <h3><span class="news-date">Nov 8, 2021</span></h3>
  <p>
    Delivered a workshop on  
    <a target="_blank" style="text-decoration: underline; color: #268bd2" href="[video-url]">
      "[Workshop Title]"</a>
    to [audience] at [location]. 
    <a target="_blank" style="text-decoration: underline; color: #268bd2" href="[additional-link]">
      <em> [Additional Resource] </em></a>
  </p>
</div>
```

### News Item Guidelines

1. **Date Format**: Use "Month DD, YYYY" format (e.g., "Jun 14, 2025")
2. **Order**: Keep most recent items at the top
3. **Tone**: Use positive, professional language (Excited, Grateful, Thrilled, Delighted)
4. **Links**: Always include relevant links when available
5. **Length**: Keep descriptions concise but informative

## Customization Tips

### Colors
The current theme uses `#268bd2` for link colors. You can change this throughout the file if needed.

### Styling
- Links have `text-decoration: underline` and open in new tabs (`target="_blank"`)
- Maintain consistent spacing and formatting
- Use `<em>` tags for emphasis on secondary links

### Content Strategy
- Keep your bio concise but informative
- Highlight your most significant achievements in recent news
- Update regularly to keep content fresh
- Remove example content once you've added your own

## File Structure

After customization, your directory should look like:
```
/assets/
  ├── img/me/[your-image-filename]
  └── [Your_CV_Filename].pdf
_includes/
  └── about.html (customized)
```

## Next Steps

1. Replace all placeholder text with your information
2. Add your profile image and CV to the assets directory
3. Test all links to ensure they work correctly
4. Preview your site locally to check formatting
5. Remove this instruction file once you're done

Remember to remove the example news items and replace them with your actual achievements!
