## Website Performance Optimization portfolio project

### Instructions for Running

To begin, either download the repository and open index.html in your own browser, or check out my github pages version at: [http://mjroncone.github.io/fend-perf-opt/](http://mjroncone.github.io/fend-perf-opt/ "Mike Roncone's optimization example").

Feel free to play around with any of the sections. There currently is not any additional functionality in the first three pages, but you will find additional things to do on the page called "Cam's Pizzeria".

In Cam's Pizzeria, you can see the background pizzas move around as you scroll through the page. You can also use the slider in the "Our Pizzas!" section to resize the picture pizzas below it. The three sizes available are small, medium, and large. But you could change the code to include any number of sizes!

### My Optimization Route: HTML(index.html and variants)

1. Google font was removed. The impact/design difference was not important enough for the performance sag.
2. All CSS was inlined. The styles.css file was not large enough to warrant blocking the rendering path.
3. Non-critical JS files were made async, which included moving the inlined analytics code to an external file and then calling it with async.
4. All images were optimized to be no larger than their largest size when painted on the screen.

### My Optimization Route: JS(pizza.html and main.js)

1. Changed pizzaElementGenerator to append pizzas as they are created, instead of returning them and appending later.
2. Fixed changePizzaSizes to eliminate the Forced Synchronous layout that it was causing.
  * Took the size switcher from the separate function and placed it inside the changePizzaSizes function. It is only used here so why keep it separate>
  * Eliminated the use of dx, because it was a weird way of performing a bunch of useless calculations by finding the difference in ratio of pizza to windowsize between
  the old and the new sizes. Instead, I just made it choose a newWidth based on a certain % from the size switcher.
3. Took document.body.scrollTop out of the updatePositions function's for loop in order to try and avoid some more FSL issues.
4. Reduced and simplified the sliding pizza generator from 8 pizzas * 25 rows to 5 pizzas * 3 rows. The way that
the sliding pizzas work, you basically had an extra 22 rows of unnecessary pizzas, as they scroll with the viewport causing a whole lot of extra painting.
5. Switched some work from painting to compositing only by making each sliding pizza have will-change: transform.

### Optimization Tips and Tricks
* [Optimizing Performance](https://developers.google.com/web/fundamentals/performance/ "web performance")
* [Analyzing the Critical Rendering Path](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/analyzing-crp.html "analyzing crp")
* [Optimizing the Critical Rendering Path](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/optimizing-critical-rendering-path.html "optimize the crp!")
* [Avoiding Rendering Blocking CSS](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/render-blocking-css.html "render blocking css")
* [Optimizing JavaScript](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/adding-interactivity-with-javascript.html "javascript")
* [Measuring with Navigation Timing](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/measure-crp.html "nav timing api"). We didn't cover the Navigation Timing API in the first two lessons but it's an incredibly useful tool for automated page profiling. I highly recommend reading.
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/eliminate-downloads.html">The fewer the downloads, the better</a>
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/optimize-encoding-and-transfer.html">Reduce the size of text</a>
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/image-optimization.html">Optimize images</a>
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/http-caching.html">HTTP caching</a>

### Customization with Bootstrap
The portfolio was built on Twitter's <a href="http://getbootstrap.com/">Bootstrap</a> framework. All custom styles are in `dist/css/portfolio.css` in the portfolio repo.

* <a href="http://getbootstrap.com/css/">Bootstrap's CSS Classes</a>
* <a href="http://getbootstrap.com/components/">Bootstrap's Components</a>

### Sample Portfolios

Feeling uninspired by the portfolio? Here's a list of cool portfolios I found after a few minutes of Googling.

* <a href="http://www.reddit.com/r/webdev/comments/280qkr/would_anybody_like_to_post_their_portfolio_site/">A great discussion about portfolios on reddit</a>
* <a href="http://ianlunn.co.uk/">http://ianlunn.co.uk/</a>
* <a href="http://www.adhamdannaway.com/portfolio">http://www.adhamdannaway.com/portfolio</a>
* <a href="http://www.timboelaars.nl/">http://www.timboelaars.nl/</a>
* <a href="http://futoryan.prosite.com/">http://futoryan.prosite.com/</a>
* <a href="http://playonpixels.prosite.com/21591/projects">http://playonpixels.prosite.com/21591/projects</a>
* <a href="http://colintrenter.prosite.com/">http://colintrenter.prosite.com/</a>
* <a href="http://calebmorris.prosite.com/">http://calebmorris.prosite.com/</a>
* <a href="http://www.cullywright.com/">http://www.cullywright.com/</a>
* <a href="http://yourjustlucky.com/">http://yourjustlucky.com/</a>
* <a href="http://nicoledominguez.com/portfolio/">http://nicoledominguez.com/portfolio/</a>
* <a href="http://www.roxannecook.com/">http://www.roxannecook.com/</a>
* <a href="http://www.84colors.com/portfolio.html">http://www.84colors.com/portfolio.html</a>
