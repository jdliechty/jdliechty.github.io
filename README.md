Phase 1:  I wanted to get a website up-and-running on GitHub with Jekyll using Jekyll's Minima 
theme but with a few adjustments:  Shorter blog-like posts would appear in a separate 
page (not on the landing page) and there would be separate pages for coding projects 
and longer documents (each with their own entry in the menus).

Started with new, empty repository jdliechty.github.io on GitHub and using Jekyll is 
installed via homebrew on local computer (running OS X).

Then in directory for webpage on local computer.

```shell
jdliechty$ jekyll new jdliechty.github.io
jdliechty$ cd jdliechty.github.io
```

And test:

```shell
jdliechty$ jekyll serve
```

Then to locate minima configuration files on the local computer:

```shell
jdliechty$ bundle show minima 
/usr/local/lib/ruby/gems/2.5.0/gems/minima-2.1.1
```

And copy the minima configuration files into local directory:

```shell
jdliechty$ cp -R /usr/local/lib/ruby/gems/2.5.0/gems/minima-2.1.1/_includes .
jdliechty$ cp -R /usr/local/lib/ruby/gems/2.5.0/gems/minima-2.1.1/_layouts .
jdliechty$ cp -R /usr/local/lib/ruby/gems/2.5.0/gems/minima-2.1.1/_sass .
jdliechty$ cp -R /usr/local/lib/ruby/gems/2.5.0/gems/minima-2.1.1/assets .
```

Initialized empty Git repository in directory for website on local computer.

```shell
jdliechty$ git init
jdliechty$ git config user.email <your-email-here>
```

Then:

```shell
jdliechty$ jekyll serve
```

and you should see the jekyll minima default website at http://127.0.0.1:4000

Added custom domain info to CNAME file...

```shell
jdliechty$ git add .
jdliechty$ git commit -m "Initial default minima install."
```

Edit title, author, etc. information in `_config.yml`

```shell
jdliechty$ touch contact.md docs.md posts.md projects.md
```

Add the following to the `_contig.yml` to designate which menus should appear and in what order:

```yml
header_pages:
  - projects.md
  - docs.md
  - posts.md
  - about.md
  - contact.md 
```

Edit about.md to read:

---
layout: page
title: about
permalink: /about/
---

and edit each respective page:

---
layout: page
title: contact
permalink: /contact/
---

---
layout: page
title: docs
permalink: /docs/
---

---
layout: page
title: posts
permalink: /posts/
---

---
layout: page
title: projects
permalink: /projects/
---

jdliechty$ touch README.md

Removed "posts" loop in _layouts/home.html
Added "posts" loop to posts.md

Make the site-title a little heavier.  In _sass/minima/_layout.scss:

.site-title {
  @include relative-font-size(1.625);
  font-weight: 300;

changed this to:
.site-title {
  @include relative-font-size(1.625);
  font-weight: 600;

and reduce the size of the page titles

In _sass/minima/_layout.scss

Changed:

.post-title {
  @include relative-font-size(2.625);


to 

.post-title {
  @include relative-font-size(1.75);


And in _layouts/default.html, commented out liquid tag for including footer:

    {% comment %}
    {% include footer.html %}
    {% endcomment %}


Then:

jdliechty$ git add .
jdliechty$ git commit -m "Changed page header font, removed footer"
jdliechty$ git push -u origin master


