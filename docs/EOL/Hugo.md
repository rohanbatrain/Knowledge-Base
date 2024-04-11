Let's Deploy our blog using Hugo. Why a separate blog? While having a knowledge base? 

I have built my knowledge base to have all the working bits, it doesn't contain all the failure which are necessary to know about while learning a new technology. So to complete this requirement i want to have a blog in which i am going to document complete start to end process of everything related to tech i do.

## Preparation

### Linux installation

I am using cachyos at the moment, i can easily install hugo using `sudo pacman -S hugo`. 


### Creating the project

1. Create a new project using `hugo new site <site-name>`
2. I am using papermod theme. Please follow the steps below to install it:

Cloning the repo

```bash
git clone https://github.com/adityatelange/hugo-PaperMod themes/PaperMod --depth=1
```

pulling the changes if there's any from the papermod origin.

```bash
cd themes/PaperMod
git pull
```

## Configuration

I used the following yaml for starting point from papermod wiki:

1. hugo.yml

```yaml
baseURL: "https://rohanbatra.in/blog/"
title: Rohan's Blog
paginate: 5
theme: PaperMod
params:
  # defaultTheme: light
  # defaultTheme: dark
  ShowShareButtons: true
  ShowReadingTime: true
  ShowToc: true
  editPost:
    URL: "https://github.com/rohanbatrain/Blog/content"
    Text: "Suggest Changes" # edit text
    appendFilePath: true # to append file path to Edit link
  defaultTheme: dark
  ShowPostNavLinks: true
  ShowCodeCopyButtons: true
  author: ["Rohan"]
  profileMode:
        enabled: true
        title: "Rohan Batra" # optional default will be site title
        #subtitle: "My Blog"
        imageUrl: "<image link>" # optional
        imageTitle: "Rohan Batra image" # optional
        imageWidth: 120 # custom size
        imageHeight: 120 # custom size
        buttons:
            - name: Donate
              url: "donate"
            - name: Github
              url: "https://github.com/rohanbatrain"
  socialIcons: # optional
        - name: "Github"
          url: "<link>"
        - name: "Instagram"
          url: "<link2>"
        - name: Rss
          url: "index.xml"
  fuseOpts:
    isCaseSensitive: false
    shouldSort: true
    location: 0
    distance: 1000
    threshold: 0.4
    minMatchCharLength: 0
    keys: ["title", "permalink", "summary", "content"]



outputs:
  home:
    - HTML
    - RSS
    - JSON # is necessary
```

2. archetypes/default.md

```yaml
---
title: "{{ replace .Name "-" " " | title }}"
date: {{ .Date }}
draft: true
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
ShowWordCount: true
ShowRssButtonInSectionTermList: true
UseHugoToc: true
---
```

3. Add the following config to content/archives.md

```yaml
---
title: "Archive"
layout: "archives"
url: "/archives/"
summary: archives
---
```

4. Make folders and files 

You would make:

* content/categories.md
* content/archive.md
* content/search.md
* content/donate.md