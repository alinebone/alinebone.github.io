---
layout: post
categories: development english
title: Semantic HTML - a brief overview
---

*Semantic markup* is a modern concept that tells us to use meaningful element names in markup languages like HTML. We are already applying this concept when we use `<strong>` instead of `<b>` to give importance to a text. However, there are several meaningful tags we should use, but keep ignoring. HTML itself has about 40 tags that only 5% of websites are making use of. Adopting meaningful elements is an important aspect of modern web development for several reasons including:  

- **Accessibility** - A variety of devices will better understand the content and because of this understanding, the content can be presented in the best way for each device, including *text-to-speech* (TTS) programs. Accessibility is job number one, every person should be able to access any public data. In fact, in many places it's illegal to make a website inaccessible to people with disabilities;
- **Search engine friendly** - Search engines, screen readers, and other machines will identify the different parts of the website more easily;
- **Maintainability** - It helps the developers to keep the website organized, making it better to maintain.

## Major elements

The first thing to do when creating a webpage is to analyze the content that is being added. It's important to understand what the page is trying to communicate to choose the right tag. Let's take a look at the six major elements on semantic HTML: `<main>`, `<header>`, `<footer>`, `<article>`, `<section>`, and `<aside>`.  

The `<main>` element, as the name suggests (and that's the point!),  wraps around the main content of the page. It's only used once per webpage, and it tells the browser where the main content is.   

The `<header>` tag represents an introduction. Most of the webpages have a header at the top containing the logo, the site name, and the navigation elements.  

It's very common to end a website with a `<footer>` element at the bottom, holding extra information about the company like address and related links. However, footers don't have to go to the bottom. Many articles start out with some metadata, a list of hashtags, or groups of share buttons. That kind of information is actually well-suited for a footer element. The fact that it might be displayed up at the top doesn't matter. It's the semantic meaning that matters, not the visual display.  

An `<article>` can be a long written article or blog post, it might be a very short cut or a teaser card. It also can be a tweet or social media post. The article element just means that it is by itself, a unit of content.  

The `<section>` tag is used to wrap around sections of content. It defines zones on our website. A section is a flexible element that means we're starting with another thing.  

The `<aside>` is for marking something that's off to the side. It can be a sidebar or any content that's not the main attraction. It could be an advertisement or an inset panel that goes with a big article giving additional information but isn't quite part of the flow of the article itself. Again, it's the semantic meaning that matters, not the position on the page.  

Summarizing, the `<main>` element is used only once per page to wrap around the main content on that page. The `<header>`, `<footer>`, `<article>`, `<section>`, and `<aside>` elements are the five sectioning elements in HTML. They are used together, nested inside of each other in patterns and combinations that give the content of a webpage its true meaning.

## Other tags

Apart from the main six elements, there are other tags that also contain semantics:  

- **Paragraph**  
  - `<p>` - as the name says, it holds a paragraph.
    

- **Headlines**   
  - `<h1>`, `<h2>`, `<h3>`, `<h4>`, `<h5>`, `<h6>` - headlines are some of the most semantic things in a web page. They play a significant role in how search engines determine what’s important on your web page.   
    

- **Highlights**  
  - **Emphasis**
    - `<em>` *(meaning)* or `<i>` *(no meaning)*. This one can be trick. To emphasize a text, use `<em>`, but if the goal is just to display the title of something, use `<i>`. e.g. My `<em>favorite</em>` movie is `<i>The Edukators</i>`. It's easier to understand if we think about reading the sentence out loud;
  - **Importance**  
    - `<strong>` *(meaning)* or `<b>` *(no meaning)*: `<strong>` means something is important or urgent. This tag can be used on the word "Warning" for instance. While `<b>` just give us a way to mark something. It's important to say that `<b>` is not recommendable, and must be used only as last resort;


- **Lists**  
    - **Unordered and ordered lists**  
        - `<ul>` *(unordered list)*: an unordered list represents a set of related items that have no special order or sequence. It can be a navbar, a shopping list, or a todo list.
        - `<ol>` *(ordered list)*: ordered lists are used when the order of the items is important. Rank items or steps of a recipe can be represented in an ordered list.
        - `<li>` *(list item)*: `<li>` elements are the content inside `<ul>` or `<ol>`.
    - **Definition list**
        - `<dl>` *(definition list)*: `<dl>` represents the definition list. This type of list works like a dictionary. We have a key/value to define elements. Must be used along with `<dt>` and `<dd>`. 
        - `<dt>` *(data term)*: work as a key
        - `<dd>` *(data description)*: work as a value   
   
   
- **Quotes**  
    - `<blockquote>`: when we are going to cite someone, we wrap the entire content in a `<blockquote>` element. Inside the `<blockquote>` we can use any kind of content, but the most common is a paragraph.
    - `<cite>`: we use this tag to cite the source of a quotation or creative work. It doesn't necessarily have to be a person.
    

- **Dates and times**
    - `<time>`: element used to mark anything that's specifying a time of day, a date, or span of time. It can wrap any human understandable format of a date. The secret of this tag is the use of the datetime attribute. Inside this attribute, we set a value that a computer can understand.


- **Code**
    - `<code>`: the `<code>` tag defines a piece of computer code.


- **Links**
    - `<a>`: this is the anchor tag, a very simple meaning. Just adding a thought about that. In the past, people were obsessed with the idea of a special zone on a page that would teleport you to another place. It took over 20 years of theorizing and experimenting until we ended up with the web in the ‘90s. The anchor tag represents this beautiful idea of magic transportation.
    - `<nav>`: specify a block of navigation links, either within the current document or to other documents. It's used only for menus. If we add the attribute role="navigation" we'll be giving it more semantic, saying that it is the main navigation.

- **Images**
    - `<img>`: holds any type of image, don't forget the alt element to give it more semantic.
    - `<picture>`: this element is a container used to set specific sources (`<source>`) for an image element to make it work well with different screen sizes.
    - Use a `<figure>` element to mark up a photo in a document, and a `<figcaption>` element to define a caption for the photo: this brings more semantic to an image.

- **Media**
    - `<audio>` and `<video>` - These tags are used to embed sound and video content in a document, such as music, other audio streams, movie clips and other video streams.
The <source> tag is used to specify media resources for audio and videos.
    - `<track>` - The `<track>` tag specifies text tracks for `<audio>` or `<video>` elements.

- **Forms**
    - `<form>` - It's used to create forms that people might use to sign up for newsletters, e-commerces, send a message to companies, or just login in a website. We can collect input fields like name, email address, and password. Inside the <form> tag we can use some self-explained tags like `<button>`, `<input>`, `<select>` and `<label>`.

- **Tables**  
    - `<table>` - You might have heard somewhere along the way that HTML tables are evil, that you should never use a table, or at least that's what some people have heard or thought they heard but it's not true. It's not bad to use an HTML table for tabular data. In fact you should use an HTML table when your content is a table, absolutely. What you should not do is misuse HTML table elements and pretend that you're making a table when you're not. The whole point of semantic HTML is to tell computers everywhere what the thing you have is. What is it? If you have a button, use the button element. If you have a table, use the table elements.

You can get away with using divs and spans for everything. Some people wrap their titles in divs. They make spans pretend to be buttons. It seems to work. HTML doesn't throw an error, it doesn't stop running. The browser will still parse the page and it will still do its best to do its job. But it's bad and it hurts a lot of users. So don't use divs and spans for everything. Use them when there's not another appropriate element as a last resort.

There's not one right way to write HTML. In fact, usually there are more than one good way to do it, and none of them are necessarily right or better. There's a bit of an art to structuring HTML. We have a lot of creative freedom here. We are, after all, trying to represent human communication in code, and while code maybe wants to be correct and perfect, human connection is not.


    


