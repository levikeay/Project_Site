# Levi Keay's project portfolio site [under development]
Find the live site [here, https://levikeay.github.io/Project_Site/](https://levikeay.github.io/Project_Site/)

Created from the Jekyll theme **WhatATheme**. Find WhatATheme's [**Demo Here**](https://thedevslot.github.io/WhatATheme/)

I hope to continue to add short writeups of past projects I have done to have a place to showcase my interests.

### Installation

I installed this theme website by forking the [WhatATheme Repository](https://github.com/thedevslot/WhatATheme/). I host the site on Github Pages, with no local Ruby/Jekyll environment!

### Writing Posts

WhatATheme has both posts and projects templates. I intend to use this site more as a project portfolio, however I have found the post template to be easier to work with. I will likely eventually remove the projects tab from my site for simplicity. 

To write a post, I start with the markdown documents provided in the _posts_ directory as a template, or create a new markdown document in that directory. When the site is built this will automatically generate a new post.

### Other changes made to the template, general tips for customization :

I've made edits to HTML files in the repository in order to style the page to my liking. This includes removing blog post dates and read times in the blog card display. 

~~- **I had to add this line to the gemfile:**~~

~~>gem "webrick"~~

~~This allows the site to build using the newest ruby update, which does not include this package natively (thank you stack exchange).~~ fixed with merge, august 2022


- **I enabled mathjax for writing LaTex style expressions following [this tutorial](https://alanduan.me/random/mathjax/).**

It involves 2 steps:
1) edit _includes/head.html and include the following lines:
 
 >{% if page.usemathjax %}
    <script type="text/javascript" async
     src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-MML-AM_CHTML">
      </script>
    {% endif %}
    
  ... copy from here with the spelling as "endif" not "end if" as the tutorial shows. Check my head.html file for the specfic formatting.

2) add : 
 
 >usemathjax: true
 
 ... to the html portion of your post which you want to use mathjax in (this is the part between the dashed lines at the top of your post.

Then envelope your math expressions with \$\$ on either side.


- **I edited about.html to change the names of the buttons, and added a button to link to my resume.**

[I found this tutorial helpful](https://bulma.io/documentation/columns/options/)

- **Use a square (1:1 ratio) author picture to allow for conversion to circle shaped figure in footer.html and about.html sections.**

- **To embed PDFs:**

I found this html code to work best:

~~~
<center>
  <embed src="https://drive.google.com/viewerng/viewer?embedded=true&url=YOUR_PDF_HERE.pdf" width="850" height="4400">
</center>
~~~

Replace YOUR_PDF_HERE.pdf with the url link to your pdf. this will be centered due to \<center\> tags. I set the width and height to be proportional to an 8.5x11 page by using width 850 and height 1100 * number of pages. The example above is for a 4 page document. This way there is no double scroll bar, and the pdf can sit inside the webpage. However, I have found that the PDF sometimes does not render in the site, depending on device or browser. Therefor I always include a link to the pdf using the common link syntax.




---
Thank you to [thedevslot](https://github.com/thedevslot/WhatATheme/) for this useful and stylish template.

---

### WhatATheme Credits :bulb:
* [Sneha Omer](http://sassyecoder.github.io/)
* [Harsh Trivedi](http://harsh98trivedi.github.io/)
