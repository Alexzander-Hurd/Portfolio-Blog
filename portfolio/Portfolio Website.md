---
title: Portfolio Website
description: An Astro static site, modified to use Obsidian as a content management system, hosting my personal blog and professional portfolio.
pubDate: Jul 6 2025
heroImage: ../../../public/images/website-hero.png
---
# Project Links: <a href="https://github.com/Alexzander-Hurd/Portfolio-Web"><img src="https://img.shields.io/badge/Web-%23121011.svg?logo=github&logoColor=white"/></a> <a href="https://github.com/Alexzander-Hurd/Portfolio-Blog"><img src="https://img.shields.io/badge/Blog-%23121011.svg?logo=github&logoColor=white"/></a>

**Quick Stats:**

- Tech stack - Astro + TypeScript, Markdown (Obsidian vault), Node.js scripts  
- CI/CD - GitHub Actions, Cloudflare Pages / DNS  
- Status - Beta (live, under slow and sporadic development)  
- Licensing - MIT (web), CC BY-NC-ND (blog)  

# Overview

This is my personal portfolio website and blog, built with Astro. It uses my Obsidian vault as a content management system, allowing me to manage posts and portfolio entries in Markdown while automatically integrating them into the website via a Git submodule.

# Purpose

I wanted a lightweight, fast, and version-controlled platform for my professional portfolio and personal blog. Using Astro with an Obsidian-based workflow allows me to write content in a familiar environment while keeping the website deployment automated and secure.

# Features

- Personal blog + professional portfolio in a single static site  
- Obsidian vault as content management system  
- Automated CI/CD pipeline via GitHub Actions → Cloudflare Pages  
- Staging builds protected by Cloudflare Zero Trust  
- Lightweight, fast static site architecture with Astro  

# Installation & Usage

This site is hosted and does not require local installation. The content is updated automatically via the Obsidian vault submodule and CI/CD workflows.

# Technical Details

- Astro static site generator with TypeScript  
- Node.js scripts for asset management and submodule updates  
- Markdown content integrated via Git submodule  
- Cloudflare Pages hosting with preview/staging builds  
- GitHub Actions workflows for automated content deployment  

# Roadmap

- Continue improving layouts and responsive design  
- Expand blog features (search, filtering, tags)  
- Enhance CI/CD workflow with button-triggered production promotion  
- Explore additional Obsidian integrations  

# License

- Web repository: MIT ([LICENSE](https://github.com/Alexzander-Hurd/Portfolio-Web/blob/master/LICENSE))  
- Blog content: CC BY-NC-ND ([LICENSE](https://github.com/Alexzander-Hurd/Portfolio-Blog/blob/master/LICENSE))  
