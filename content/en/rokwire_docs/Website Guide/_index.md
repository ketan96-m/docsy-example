---
title: "Website Guide"
linkTitle: "Website Guide"
weight: 4
description: > 
    Guide on how to implement the docsy website and deploy
---
<link rel = 'stylesheet' href = '/css/image_style.css'></link>

## How to setup the Docsy-theme:

### Setup GoHugo

Download GoHugo **extended** version from the [link.](https://github.com/gohugoio/hugo/releases)

Make sure to download the extended version. For this setup the Hugo was downloaded on windows.

<img src="/image/Website_guide_1.png">

Once you download the file.

Follow the instructions on this [link.](https://gohugo.io/getting-started/installing/#windows)

Open command prompt and type in _hugo version_

If the installation is correct, it will display the hugo version.

<img src="/image/Website_guide_2.png">

### Create the Docsy-theme sample website:

To create the docsy-theme clone or follow the instructions on this [site](https://github.com/google/docsy-example) to setup.

<img src="/image/Website_guide_3.png"> 

     git clone --recurse-submodules --depth 1 \<forked-docsy-example-repo\>

Next install NPM packages like

    autoprefixer@10.4.2

    postcss-cli@9.1.0

    [postcss@8.4.6](mailto:postcss@8.4.6)

To install, first install Node.JS from [https://nodejs.org/en/download/](https://nodejs.org/en/download/)

After installation, use `npm install` to install the above 3 packages

    npm install autoprefixer

    npm install postcss

    npm install postcss-cli

Check if the packages are installed using
    
    npm list

<img src="/image/Website_guide_4.png">

After you install the npm modules and the git submodule you are good to begin constructing the website

    hugo server

This will create the sample example website

Go to the local port **//localhost:1313/**

<img src="/image/Website_guide_5.png">

<img src="/image/Website_guide_6.png">

**Edit the website**

Use a text editor to manipulate the website content

The vanilla website will have some of the folders below

Go to the [link](https://www.docsy.dev/docs/) below to the detailed instruction to edit the website

https://gohugo.io/getting-started/directory-structure/ 

<img src="/image/Website_guide_7.png">
<img src="/image/Website_guide_8.png">
<img src="/image/Website_guide_9.png">
<img src="/image/Website_guide_10.png">
<img src="/image/Website_guide_11.png">

Add this line to top of every markdown file to use the css style sheet

<img src="/image/Website_guide_12.png">

All the markdown files sit in the Content folder.

<img src="/image/Website_guide_13.png">

There are 3 sub folder which give the language of each file in it. For now, we are focusing on the English language.

<img src="/image/Website_guide_14.png">

To get the Rokwire Documentation in the menu; create a new folder in _en_ directory

Like `en\rokwire\docs\`

Next create an `_index.md` file to give title and weight

### Page frontmatter

Each page file in a Hugo site has metadata frontmatter that tells Hugo about the page. You specify page frontmatter in TOML, YAML, or JSON (our example site and this site use YAML). Use the frontmatter to specify the page title, description, creation date, link title, template, menu weighting, and even any resources such as images used by the page. You can see a complete list of possible page frontmatter in [Front Matter](https://gohugo.io/content-management/front-matter/).

For example, here&#39;s the frontmatter for this page:

<img src="/image/Website_guide_15.png">

The weight given decides at what position the Rokwire Documentation will be placed. Higher the weight, the section will be displayed more towards the right. In this case Rokwire Documentation has weight 25 which is to the right of Documentation, which has a weight of 20.

<img src="/image/Website_guide_16.png">

The link title displays what is displayed before clicking on the section.

The title displays the title of the page once you click on the link

Let&#39;s take an example:

<img src="/image/Website_guide_17.png">

<img src="/image/Website_guide_18.png">

<img src="/image/Website_guide_19.png">

<img src="/image/Website_guide_20.png">

Hugo builds your site pages using the content files you provide plus any templates provided by your site&#39;s theme. These templates (or _&quot;layouts&quot;_ in Hugo terminology) include things like your page&#39;s headers, footers, navigation, and links to stylesheets: essentially, everything except your page&#39;s specific content. The templates in turn can be made up of _partials_: little reusable snippets of HTML for page elements like headers, search boxes, and more.

Because most technical documentation sites have different sections for different types of content, the Docsy theme comes with the [following templates](https://github.com/google/docsy/tree/master/layouts) for top-level site sections that you might need:

- [docs](https://github.com/google/docsy/tree/master/layouts/docs) is for pages in your site&#39;s Documentation section.
- [blog](https://github.com/google/docsy/tree/master/layouts/blog) is for pages in your site&#39;s Blog.
- [community](https://github.com/google/docsy/tree/master/layouts/community) is for your site&#39;s Community page.

Mention the type of doc in the frontmatter

As type: `docs`

If you want all the documents in the same directory to have the same type use the keyword &quot;cascade&quot;.

<img src="/image/Website_guide_21.png">

You can place your Markdown files as you please in the folder as per your hierarchy.

<img src="/image/Website_guide_22.png">

Here the hierarchy follows like this

`User guide>getting_started>setup>_index.md`

**Format all images together**

To format all images together create css file in the static folder and you can also store all your images in a single folder. You can then import the same css file to format your content on each page.

<img src="/image/Website_guide_23.png">

Here, the image\_style.css is used as a stylesheet to format all the images in markdown.

When accessing static folder content, you don&#39;t need to give the complete path to the file.

You provide a path like this - `/css/image_style.css`

_ **The forward slash implicitly tells Hugo to take the file from the static folder.** _

Headings within the same page

Hugo allows you navigate to different section within the same page. It has sections on the right side of the window which are hyperlink to their respective headings.

<img src="/image/Website_guide_24.png">

This allows the user to have breakdown of their content page so that the reader can easily navigate to different points in the same page. Achieving this is very simple, and you only need to create **headers** in the markdown file. For example

<img src="/image/Website_guide_25.png">

The above stub will create clickable link on right automatically while also creating the traditional header for that section.

**Deploy to Netlify**

Once you done with editing the content on the webpage push your changes to the remote repo like Github.

Before deployement create netlify.toml file in your root directory which has the following content

<img src="/image/Website_guide_26.png">

    [build]

    command = "cd themes/docsy && git submodule update -f --init && cd ../.. && hugo --gc --minify"

    [build.environment]

    HUGO\_VERSION = <local_hugo_version>

The build command is very important because it will tell netlify to which theme, which version of hugo you are using.

You can get the version of your Hugo by typing in Hugo version in terminal or cmd.

Once you create the file and save it, then go to [https://www.netlify.com](https://www.netlify.com/)and login.

On the sites tab, click on Import from Git

<img src="/image/Website_guide_27.png">

<img src="/image/Website_guide_28.png">

Follow the onscreen instructions and click on deploy the site.

You can click on preview to check the website live.

Anytime you commit anything new to the Github, due to continuous integration, Netlify will build the site automatically for that commit.