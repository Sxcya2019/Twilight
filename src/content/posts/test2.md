---
title: 搭建Astro博客教程丨Cloudflare worker/pages丨优选域名
published: 2026-07-25
updated: 2026-07-25
description: 2026.7.25
category:
  - Tutorials
draft: false
---
So you built your blog with the Twilight Astro theme. Now you want to put it online so other people can see it. This guide will show you exactly how to do that.

I will cover 5 different ways to deploy your site. You only need to pick one. If you are a beginner, start with GitHub Pages or Netlify. They are the easiest.

Before you start, make sure you have:

- Your Twilight Astro project on your computer
- A GitHub account (free)
- Your project pushed to a GitHub repository

---

**## 1. Deploy to GitHub Pages (Free, Automatic)**

GitHub Pages is free. The Twilight theme already has a built-in auto-deploy script. You only need to turn it on.

**Step 1: Enable GitHub Pages**

Go to your GitHub repository. Click **Settings** > **Pages**. Under "Build and deployment," change the **Source** dropdown to **GitHub Actions**.

**Step 2: Push your code**

Open your terminal. Run these commands:

```
git add .
git commit -m "First deploy"
git push origin main
```

**Step 3: Wait for the build**

Go to the **Actions** tab in your GitHub repository. You will see a workflow running. Wait 1-2 minutes. When you see a green checkmark, your site is live.

Your site URL will be: [https://your-username.github.io](https://your-username.github.io)

**Optional: Use your own domain**

Edit the file `public/CNAME` in your project. Write your domain name inside, for example:

```
blog.yourname.com
```

Then go to your domain provider's DNS settings. Add a CNAME record that points to `your-username.github.io`. Push your code again. Done.

---

## 2. Deploy to Cloudflare Pages (Fast, Global CDN)

Cloudflare Pages is free and fast because it uses servers all over the world.

**Step 1: Connect your GitHub repo**

Log in to your Cloudflare account. Go to **Workers and Pages** > **Create application** > **Pages** > **Connect to Git**. Authorize Cloudflare and select your Twilight repository.

**Step 2: Set build options**

Cloudflare will detect Astro automatically. Check that these values are correct:

- Build command: `npm run build`
- Output directory: `dist`

**Step 3: Deploy**

Click **Save and Deploy**. Wait 2-3 minutes. Your site will be live at: [https://your-project-name.pages.dev](https://your-project-name.pages.dev)

**If you use DecapCMS**: Go to your project settings in Cloudflare, find **Environment variables**, and add the contents of your `.env` file there.

---

## 3. Deploy to Netlify (Beginner Friendly)

Netlify is very easy to use. The interface is clean and simple.

**Step 1: Import your project**

Go to the Netlify dashboard. Click **Add a new site** > **Import an existing project**. Connect your GitHub account and select your Twilight repository.

**Step 2: Configure**

Netlify will detect Astro automatically. Confirm these settings:

- Build command: `npm run build`
- Publish directory: `dist`

**Step 3: Deploy**

Click **Deploy site**. Netlify will give you a random URL like [https://random-name-123abc.netlify.app](https://random-name-123abc.netlify.app). You can change it later in Site settings.

---

## 4. Deploy to Vercel (One Click)

Vercel is very similar to Netlify. It is also beginner friendly.

**Step 1: Import your repository**

Go to [https://vercel.com](https://vercel.com) and log in with GitHub. Click **Add New** > **Project**. Find your Twilight repository and click **Import**.

**Step 2: Deploy**

Vercel will detect Astro automatically. Leave the default settings and click **Deploy**. It takes about 1 minute.

Your site URL will be: [https://your-project.vercel.app](https://your-project.vercel.app)

**If you use DecapCMS**: Add your `.env` file contents to **Environment Variables** in your Vercel project settings.

---

## 5. Deploy to Your Own Server (Manual)

If you already have a server, you can deploy manually.

**Step 1: Build the site**

Open your terminal in the project folder and run:

```
npm run build
```

This creates a `dist` folder with all your static files.

**Step 2: Upload the files**

Zip the `dist` folder. Upload it to your server using FTP, SCP, or any file transfer tool.

**Step 3: Configure the web server**

For **Nginx**, use this configuration:

```
server {
    listen 80;
    server_name yourdomain.com;
    root /path/to/your/dist;
    index index.html;
    location / {
        try_files $uri $uri/ /index.html;
    }
}
```



For **Apache**, point the document root to your `dist` folder. No extra setup is needed because it is a static site.

---

## Quick Comparison


| Platform | Best For | Free Tier |
| ---------------- | ---------------------- | ----------------------------------------- |
| GitHub Pages | All-in-one with GitHub | 1GB storage, 100GB bandwidth/month |
| Cloudflare Pages | Global speed | Unlimited bandwidth, 500 builds/month |
| Netlify | Beginners, easy setup | 100GB bandwidth, 300 build minutes/month |
| Vercel | One-click deploy | 100GB bandwidth, 6000 build minutes/month |
| Self-hosted | Full control | Depends on your server |


If you are not sure which one to pick, start with **GitHub Pages**. It is free, it is already set up for Twilight, and you just need to push your code.

---

## Summary

1. Push your code to GitHub
2. Enable GitHub Pages in repo settings (Source: GitHub Actions)
3. Wait for the automatic build to finish
4. Visit your site at [https://your-username.github.io](https://your-username.github.io)

That is all you need to do. The Twilight theme handles the rest automatically.

---

*This guide is based on the [Twilight Theme Official Documentation](https://docs.twilight.spr-aachen.com/guide/deployment/).*

