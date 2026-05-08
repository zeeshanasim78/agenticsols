========================================================================
  AgenticSols Blog — Content Management Panel: Publishing Guide
========================================================================

This guide explains how to publish, edit, and manage blog posts using
the built-in Content Management Panel (CMS).

IMPORTANT — Static Site Notes
------------------------------------------------------------------------
This blog runs ENTIRELY in the browser (no backend, no database). That
means:
  • Blog posts and admin credentials are stored in YOUR browser only
    (via localStorage). They are NOT shared across devices or visitors.
  • To make blogs publicly visible to all visitors of the live site,
    you need to either (a) ask your developer to enable Lovable Cloud
    and migrate to a real database, or (b) export your posts and have
    them deployed into the codebase.
  • Password resets via email are NOT possible without a backend. A
    one-time recovery code is generated for you instead — keep it safe.


1. ACCESSING THE CMS
------------------------------------------------------------------------
   • Open your website and visit:   /admin/login
   • OR click "Admin" in the footer.

   First-time login (default credentials):
     Username:  adminuser
     Password:  2119691

   On your VERY FIRST login, the panel shows a one-time recovery code.
   COPY IT and store it somewhere safe (password manager, paper notebook).
   You will need this code if you ever forget your password.


2. CHANGING YOUR PASSWORD AND USERNAME
------------------------------------------------------------------------
   1. Sign in.
   2. Click "Settings" in the dashboard top-right.
   3. Update username, recovery email, or password.
   4. After changing your password, you'll be signed out automatically.
      Sign back in with your new password.

   To generate a NEW recovery code (invalidates the old one):
     Settings → "Generate new recovery code" → save it immediately.


3. RESETTING A FORGOTTEN PASSWORD
------------------------------------------------------------------------
   1. Visit:  /admin/forgot-password
   2. Enter your recovery code (the one you saved at first login).
   3. Set a new password.
   4. Sign in with the new password.

   If you've lost your recovery code AND your password, contact your
   developer — they can clear browser storage to reset to defaults
   (adminuser / 2119691).


4. CREATING A NEW BLOG POST
------------------------------------------------------------------------
   1. From the dashboard, click "New post" (top-right).
   2. Fill in:
        • Title          — Keep under 60 characters for best SEO.
        • URL slug       — Auto-generated from the title; you can edit.
        • Excerpt        — A 1–2 sentence summary (max 220 chars).
                           This is used as the SEO meta description.
        • Author         — Defaults to "AgenticSols Team".
        • Tags           — Comma-separated, e.g. "AI Agents, Automation".
        • Cover image    — Optional. Max 2MB. Stored as base64.
   3. Write your content using the rich-text editor. The toolbar lets
      you add:
        • Bold, italic, strikethrough, inline code
        • Headings (H1, H2, H3)
        • Bullet & numbered lists, blockquotes
        • Images (uploaded from your device, max 2MB each)
        • YouTube/Vimeo videos (paste the URL)
        • Links (open in new tab automatically)
   4. Toggle "Published" on (in the right sidebar) to make it visible.
      Leave it off to save as a draft.
   5. Click "Save post".

   Published posts appear at:
     • /blog                        (all posts)
     • /blog/your-post-slug         (individual post)
     • Homepage "Latest from the Blog" section (newest 3 only)


5. EDITING OR DELETING A POST
------------------------------------------------------------------------
   In the dashboard:
     • "Edit"      — opens the editor with the post loaded.
     • "Publish" / "Unpublish" — toggles visibility instantly.
     • "Delete"    — permanently removes the post (asks for confirmation).


6. ADDING IMAGES, VIDEOS, AND ANIMATIONS
------------------------------------------------------------------------
   IMAGES
     In the editor toolbar, click the image icon and pick a file.
     • Max size: 2MB per image (base64 encoded into the post).
     • Use compressed JPG/WEBP for best performance.

   VIDEOS (YouTube / Vimeo)
     In the toolbar, click the YouTube icon and paste the video URL.
     The video is embedded responsively.

   ANIMATIONS / GIFs
     • Animated GIFs: upload them via the image button (treated as images).
     • Lottie / CSS animations: not supported directly in the editor.
       Ask your developer to embed them as a custom block if needed.


7. SEO BEST PRACTICES
------------------------------------------------------------------------
   The CMS automatically generates per-post:
     • <title> tag                (title + " | AgenticSols Blog")
     • <meta name="description">  (your excerpt, capped at 160 chars)
     • Canonical URL              (the full /blog/slug URL)
     • Open Graph + Twitter Card  (for nice link previews on social)
     • JSON-LD BlogPosting schema (Google rich results)

   Tips for great SEO:
     • Title under 60 characters with your main keyword near the start.
     • Excerpt under 160 characters, written as a sentence.
     • Use ONE H1 (the title is the H1 — don't add another in content).
     • Use H2/H3 for content sections.
     • Always add alt text — when uploading images via the editor,
       you can edit the HTML if you need custom alt text.
     • Internal links to other posts boost SEO.


8. SECURITY NOTES
------------------------------------------------------------------------
   • Your password is stored as a SHA-256 hash in browser storage.
   • Sessions expire after 8 hours of inactivity.
   • All blog content is sanitized with DOMPurify before display
     (prevents XSS attacks from pasted/embedded HTML).
   • Form inputs are validated with Zod (length, type, format).

   ⚠️ Because this is a static site, anyone with code access could
   inspect localStorage. For sensitive content, use Lovable Cloud
   (real authentication, role-based access, encrypted storage).


9. BACKING UP YOUR POSTS
------------------------------------------------------------------------
   To export your posts manually:
     1. Open browser DevTools (F12) → Application → Local Storage.
     2. Find the key:  wds_blog_posts_v1
     3. Copy the JSON value and save it to a file.

   To restore: paste the JSON back into the same key.


10. SUPPORT
------------------------------------------------------------------------
   • Email:    webdevsols@gmail.com
   • WhatsApp: +92 321 2119691

========================================================================