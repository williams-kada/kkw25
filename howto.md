# How this website was made

My previous website is [here](https://kkw25.user.srcf.net/). It is no longer in use, but has not been taken down. I made it using Typora, which is an editor for Markdown files (whose file extension is .md) and can generate .html files. These were the files that I then uploaded to the SRCF server.

This website is hosted by GitHub. It can display a website from .md files, although this requires a few minutes to deploy. The GitHub editor previews LaTex equations, but won't display these on the website by default.

One way to support LaTex on the website is using Jekyll, which builds a website from a depository of Markdown files. To do this, I created a file named `_config.yml` that configures the Jekyll theme. It is a one-liner:
```theme: jekyll-theme-slate```
Then, as instructed by ChatGPT (in response to a very clearly written prompt), I created a file `_includes/head-custom.html` that reads as follows:
```
<script>
window.MathJax = {
  tex: {
    inlineMath: [['$', '$'], ['\\(', '\\)']],
    displayMath: [['$$', '$$'], ['\\[', '\\]']]
  },
  svg: {
    fontCache: 'global'
  }
};
</script>

<script
  id="MathJax-script"
  async
  src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-svg.js">
</script>
```
Finally, I waited for the website to be deployed. It now displays LaTex according to MathJax, which supports many of the packages that are used in a typical document written in LaTex.

---
[index](https://williams-kada.github.io/kkw25/)
