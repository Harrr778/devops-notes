---
Title: Git Theory
date:
---
### CVCS Centralized Versioning System

A centralized version control system (VCS) uses **a single, central repository** to store all file versions and their change history. Team members have their own working copies, but all modifications are ultimately committed to this central server. This facilitates collaboration by providing a single source of truth, but it also creates a single point of failure. Examples include [Subversion (SVN)](https://subversion.apache.org/) and [CVS](https://www.nongnu.org/cvs/).

![[CVCS-Diagram.svg]]


### DVCS - Decentralized Version Control System

In a Decentralized Version Control System (DVCS), **every user has a complete copy of the repository**, including its entire history. This eliminates the reliance on a central server, allowing for offline work and greater flexibility. Changes are shared between repositories as needed. Popular examples include [Git](https://git-scm.com) and [Mercurial](https://www.mercurial-scm.org/).

![[DVCS-Diagram.svg]]

### What is Git?
Git is like a super-powered tracking system for your files and the changes you make to them over time. Imagine it as a special folder that remembers every version of your work, allowing you to go back to any previous stage if needed.  

Here's what makes Git special:

- **Keeps a detailed history:** Git meticulously records every change you make to your files, who made it, and when. This history helps you understand how your project evolved.  
- **Branching and merging:** Git allows you to create separate branches, like alternate timelines, to experiment with new features or try different ideas without affecting the main project. You can then merge these branches back into the main project when you're ready.  
- **Collaboration made easy:** Git is designed for teamwork. Multiple people can work on the same project simultaneously, and Git helps manage and integrate everyone's contributions smoothly.  
- **Offline access:** You have the entire project history on your computer, so you can work even without an internet connection.  
- **Popular and widely used:** Git is the most popular version control system in the world, used by countless developers and companies.  


### History of Git

Git was created by **Linus Torvalds**, the famous creator of the Linux operating system, in *2005*. He needed a better tool to manage the Linux kernel development, as the existing version control systems were not efficient enough for such a large and complex project.

Here's a glimpse of Git's history:

- **Early Days (2002-2005):** Linux kernel development relied on a proprietary DVCS called [BitKeeper](https://www.bitkeeper.org/). *When its free-of-charge use was revoked, Torvalds decided to create his own version control system*, with the goal of being faster, simpler, and more robust.
- **Birth of Git (April 2005):** Torvalds began work on Git and within a remarkably short period, had a functional system ready to manage the Linux kernel.
- **Community Takes Over (July 2005):** Junio Hamano took over the maintenance of Git, guiding its development and shaping it into the mature system it is today.
- **Widespread Adoption:** Git's speed, flexibility, and powerful features quickly gained popularity among developers. It became the preferred choice for open-source projects and eventually spread to commercial software development.

Today, **Git is the most widely used version control system worldwide**, powering the development of countless software projects, from small personal projects to massive corporate endeavors.

