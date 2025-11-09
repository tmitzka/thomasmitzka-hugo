---
draft: false
title: "Website of PyCon Austria"
slug: "website-pycon-austria"
date: 2025-10-15
summary: "Insights about the website I created for the IT conference PyCon Austria."
tags: ["PyCon Austria", "Python", "Pelican", "WordPress", "Project"]
showTableOfContents: true
---

2025 marked the first-ever **PyCon Austria** – a new IT conference dedicated to the programming language **Python**. I was responsible for designing and developing the website for the event. My goal was to create a platform that was easy to maintain and reflected the spirit of the community.

## Requirements

- Display all talks and workshops, each linked to their respective speakers  
- Enable quick updates of content such as profile photos and session start times  
- Provide an easy-to-use backend for the organizing team

---

## Implementation with WordPress

As the technical foundation, I used **WordPress** in combination with the [**JetPlugins**](https://crocoblock.com/) suite.

JetPlugins makes it possible to define *Custom Post Types* (CPTs) — custom content types that go beyond standard posts. This allowed me to tailor the CMS precisely to the needs of the conference. For example, the *“Speakers”* CPT included fields for photos, biographies, and social media profiles, while the *“Workshops”* CPT stored start times and target audiences (e.g., beginners or advanced users).

JetPlugins also provides the option to define relationships between CPTs. Each talk or workshop could be linked in the backend to one or more speakers, allowing short speaker profiles to appear automatically beneath each session description on the frontend.

![View of the “PyCon Austria 2025” website](pycon-austria-2025-website.webp "Website of PyCon Austria 2025 (WordPress)")

Overall, the website worked well and received positive feedback from both organizers and attendees.
However, one challenge became clear: speakers, talks, and workshops were **managed exclusively in WordPress**, without integration to the system used for submissions.

At conferences like PyCon Austria, talks are submitted through a *Call for Papers*.  
These submissions are reviewed on an external platform. Any changes to titles, descriptions, or personal details had to be manually updated in WordPress — an unnecessary amount of work.

---

## Relaunch as a static website

For **PyCon Austria 2026**, I wanted to make the website simpler and more flexible.  
The solution: a **Static Site Generator** instead of a CMS. Static websites do not require a database or regular updates, making them faster and more secure.

Given Python as the theme of the conference, I chose [**Pelican**](https://getpelican.com/), a Python-based static site generator. The editorial team now edits pages directly as **Markdown files**, without any login or backend.

In consultation with the organizers, I also redesigned the website structure:  
The main domain [**pycon.at**](https://pycon.at) serves as a central landing page, while the annual conference websites are hosted on subdomains. This setup simplifies archiving and allows each year to have an independent design.

For 2025 and 2026, I used the [pelican-bootstrap3](https://github.com/getpelican/pelican-themes/tree/master/pelican-bootstrap3) theme and customized it with CSS. Instead of the default font, the site uses *Source Sans*, a highly readable open-source font.

![View of the “PyCon Austria 2026” website](pycon-austria-2026-website.webp "Website of PyCon Austria 2026 (Pelican)")

Using a plugin, Pelican imports speaker details from a YAML file to display them on the static pages.
The relationships between talks, workshops, and speakers are defined in the **metadata of the Markdown files**.
To ensure changes are traceable, the project is managed in a **Git repository**.

### Advantages of the new website

- All content is stored as text files – Markdown for pages, YAML for speaker data.  
- Changes appear online in under a minute: generate content in Pelican, deploy, done.  
- Version control via Git makes team collaboration easier.  
- No logins, no database, no updates — overall lower maintenance effort.
