# 🔥 Network Performance

<img src="./assets/images/nw_performance.png" alt="n/w Performance" width="700" height="400">

---

## ⚡Shrunk files

<img src="./assets/images/nw_performance_3.png" alt="n/w Performance" width="700" height="400">

> We can **minify(reduce size)** javascript, html and css files by removing unnessary spaces and new lines.

?> Simple tools to minimize js, html, css files:<br>
https://javascript-minifier.com/ <br>
https://cssminifier.com/ <br>
https://html-minifier.com/

> We have to pick right format(jpg, png, svg, gif) of image for our requirement and compress them into smaller size. 

[Reference](https://www.sitepoint.com/gif-png-jpg-which-one-to-use/)

<img src="./assets/images/images_1.png" alt="images" width="700" height="400">

?> Simple tools to minimize images:<br>
https://tinypng.com/ <br>
http://jpeg-optimizer.com/ <br>

1. Try to choose simple illustrations over high detailed photographs.
2. Always lower JPEG image quality (30% - 60%)
3. Resize image based on size it will be displayed.
4. Display different sized images for different backgrounds(screens) with css media queries.
5. Use CDNs like [imigx](https://www.imgix.com)
6. Remove image meta data using tools like [verexif](http://www.verexif.com/en)

?>Using techniques mentioned above, we can reduce significant amount of data transfer between client and server. 😃

## ⚡Make Less trips

We can minimize middle delivery man👨‍🚀(network) trips(http requests) between client and server by following below mentioned steps.

1. Try to avoid 3rd party libraries with so much extra functionality, which you won't use. Instead try to choose libraries with less size.
2. Try to combine all javascript files into 1 js files. This will limit delivery man to make only one trip(http request)🏃🏽‍♂️.
3. Try to combine all css files into 1 css files for easy delivery.




