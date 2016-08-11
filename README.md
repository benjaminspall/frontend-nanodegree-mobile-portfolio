## Website Performance Optimization Portfolio 

This portfolio comes as part of Udacity's Front-End Nanodegree Website Performance Optimization project, in which we were tasked to optimize the critical rendering path on two pages: ```index.html``` and ```views/pizza.html```.

### Getting Started

To get started click the 'Download ZIP' button in the top-right of this repository's master branch, unzip its contents, then cd into the project's folder on the command line.

Next, set up a simple HTTP server with Python by running the following command:

```bash
$> cd /path/to/your-project-folder
$> python -m SimpleHTTPServer 8080
```

Open a browser and visit localhost:8080.

Now download and install [ngrok](https://ngrok.com/) to the top-level of the project directory to make the local server accessible remotely.

``` bash
$> cd /path/to/your-project-folder
$> ./ngrok http 8080
```

And you're done! Copy the public URL ngrok gives you and paste it into your browser.

### Optimizations

The following optimizations were made to this project in order to optimize the critical rendering path.

Optimizations to ```index.html```

- Removed the ‘Open Sans’ web font in favor of Arial.
- Removed ```css/style.css``` and placed it inside ```index.html``` so another file doesn't have to be fetched.
- Added ```media=“print”``` to ```<link href="css/print.css" rel="stylesheet">``` so it’s only loaded when someone wants to print the page.
- Async’d ```analytics.js```
- Minified all non-image files.
- Reduced the size of, then compressed and removed metadata from all images using [ImageOptim](https://github.com/ImageOptim/ImageOptim).

Optimizations to moving background pizzas on ```views/pizza.html```

- Reduced background pizzas from 200 to 32.
- Moved ```(document.body.scrollTop / 1250)``` calculation from for loop to ```var top```
- Changed ```document.querySelectorAll('.mover’);``` to ```document.getElementsByClassName('mover’);```
- Minified all non-image files.

Optimizations to the pizza slider on ```views/pizza.html```

- Moved ```var dx = determineDx(document.querySelectorAll(".randomPizzaContainer"), size);``` in ```changePizzaSizes(size)``` function outside of the for loop.
- Moved ```var newwidth``` outside of the for loop.
- Moved ```document.getElementsByClassName("randomPizzaContainer")``` outside of the for loop and placed into ```var pizzaBox```
- Minified all non-image files.