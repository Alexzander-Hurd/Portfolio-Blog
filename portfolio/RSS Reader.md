---
title: RSS Reader
description: A personal feed aggregator built in ASP.NET Core MVC with a simple UI for managing and reading feeds efficiently.
pubDate: Aug 14 2025
heroImage: ../../../public/images/rss_reader-hero.png
---
# Project Link: <a href="https://github.com/Alexzander-Hurd/RSS-Reader"><img src="https://img.shields.io/badge/GitHub-%23121011.svg?logo=github&logoColor=white"/></a>

**Quick Stats:**

- **Tech stack:** ASP.NET Core MVC, SQLite, C#, HTML/CSS/JS
    
- **Current version:** WIP (core RSS features working)
    
- **Planned features:** JSON feed + API support, webhooks, plugin architecture, PWA mode
    
- **GitHub stars/forks/issues:** 
<p><a href="https://github.com/Alexzander-Hurd/RSS-Reader/stargazers">
  <img src="https://img.shields.io/github/stars/Alexzander-Hurd/RSS-Reader?style=for-the-badge" alt="GitHub stars" />
</a>
<a href="https://github.com/Alexzander-Hurd/RSS-Reader/network/members">
  <img src="https://img.shields.io/github/forks/Alexzander-Hurd/RSS-Reader?style=for-the-badge" alt="GitHub forks" />
</a>
<a href="https://github.com/Alexzander-Hurd/RSS-Reader/issues">
  <img src="https://img.shields.io/github/issues/Alexzander-Hurd/RSS-Reader?style=for-the-badge" alt="GitHub issues" />
</a>
<a href="https://github.com/Alexzander-Hurd/RSS-Reader/blob/master/LICENSE">
  <img src="https://img.shields.io/github/license/Alexzander-Hurd/RSS-Reader?style=for-the-badge" alt="GitHub license" />
</a></p>

# Overview

**THIS PROJECT IS A WORK IN PROGRESS, SOME FUNCTIONALITY MAY NOT YET BE AVAILABLE**

A self-hosted, personal feed aggregator built in **ASP.NET Core Razor MVC**. Designed to ingest traditional **RSS feeds**, modern **JSON feeds**, and **webhook-based push sources**, with modular mapping support and a plugin-friendly architecture.

# Purpose

I personally enjoy the idea of RSS feeds but have found in recent years their presence around the web has drastically decreased, being replaced by next-generation JSON feeds or specific APIs. This shift makes many existing feed aggregation tools much less effective.

I thought building a modular and extensible feed aggregator, designed with the new generation of data feeds in mind, would be a fun and interesting project. Plus even if nobody else uses it, I'll have my own way to keep up with tech and security news.

# Demo


![[rss_reader-demo.gif]]

# Features

In the current state the application, as shown by the demo above, you can perform the following actions:

- Add RSS feeds
- Remove feeds
- Load articles on page request *(background job planned - see Roadmap section)*
- View articles both internally and externally depending on the information available in the XML

# Installation & Usage

Currently ASP.NET Core 8.0+ is required, this will change when Docker is implemented

```bash
# Clone the repository
git clone https://github.com/Alexzander-Hurd/RSS_Reader.git
cd RSS-Reader

# Install dependencies (for ASP.NET Core)
dotnet restore
dotnet run
```

# Technical Details

Built on ASP.NET Core MVC with minimal dependencies to keep it as light as possible, lightweight SQLite database and Docker deployment for portability *(coming soon - see next section)*, this aims to be easy to run anywhere and easy to drop into existing service stacks (especially when deployed behind a reverse proxy like Nginx to leverage powerful server-side caching).

# Roadmap

The following is a list of some of the top level goals, for a more in depth look at my feature plans see the [ROADMAP.md](https://github.com/Alexzander-Hurd/RSS-Reader/blob/master/ROADMAP.md) on the project [GitHub](https://github.com/Alexzander-Hurd/RSS-Reader)

- Introduce JSON feeds - starting with statically chosen feeds
- Add basic filtering and search - making it easier to find things that matter
- Implement schema mapping for JSON sources - allowing custom mapping of fields to my RSS feed model means users can broaden what JSON feeds are possible to integrate
- Support JSON based APIs - by expanding the schema customisation and accepting API tokens
- Include Webhook support - at first with a static schema and eventually allowing custom schema maps
- **Add PWA SUPPORT** - this one is a big one for me, I want something centrally managed and synced that's easy to access from web and mobile
- Build a plugin architecture - there are things that might not be important to me but other people would love, so I planned from the beginning to make something extensible as soon as I get to a project that can stand on its own

# Contributing

I don't have any official contribution guidelines as this is my first proper open source project, however if you have an idea for the roadmap or want to help implement a feature pull requests are more than welcome.

Once the plugin architecture is finished I plan to include some favourites in the repository itself so when that happens applications will be via pull request merging your plugin to the plugins directory.

# License

Distributed under the MIT License. See [`LICENSE`](https://github.com/Alexzander-Hurd/RSS-Reader/blob/master/LICENSE) for more information.

### WIP Notice

_As I said at the start, this project is a work in progress and therefore so is this post. As the state of the project changes I will come back and update this document to keep up to date._