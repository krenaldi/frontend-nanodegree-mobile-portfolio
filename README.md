## Website Performance Optimization portfolio project


####Part 1: Optimize PageSpeed Insights score for index.html

1. Check out the repository
2. To inspect the site on your phone, you can run a local server

  ```bash
  $> cd /path/to/your-project-folder
  $> python -m SimpleHTTPServer 8080
  ```

3. Open a browser and visit localhost:8080
4. Downloaded and installed [ngrok](https://ngrok.com/) to make your local server accessible remotely.

  ``` bash
  $> cd /path/to/your-project-folder
  $> ngrok 8080
  ```

5. Copied the public URL ngrok gave me and ran it through PageSpeed Insights.
6. Made the following changes to index.html:
- Inlined style.css in header
- add media="print" for print.css so it will call this CSS only when printing
- removed link to Open Sans fonts since font style was already declared in the stylesheet
- moved js to the end of body
- added async for scripts
- modified pizzeria pic to be 100px in width in PhotoShop so the browser did not have to work on resizing the image itself

7. Optimized all other pics displayed on this page using PhotoShop and saved them to the img directory so that the browser did not have to go to another server to pull the images.
8. Minified the final page using the following site: 
    http://www.willpeavy.com/minifier/

####Part 2: Optimize Frames per Second in pizza.html

To optimize views/pizza.html, you will need to modify views/js/main.js until your frames per second rate is 60 fps or higher. 

1. For updatePosition() function, changed querySelectorAll to getElementsByClassName which is faster. Moved the variable calling layout property scrollTop out of for-loop since it's retriggering a layout change. Created new variable top to cache document.body.scrollTop. Then added an array since Math.sin((document.body.scrollTop / 1250) + (i % 5)) generates the same the same 5 values. Used the array to optimize the for-loop to call these values when triggering the style changes to the background pizzas.
2. In the CSS file, I added   transform: translateX(0); and backface-visibility: hidden; to the .mover class so it would generate seperate layers for the background pizzas.
3. For changePizzaSizes() function, added new variable randomPizza to replace document.querySelectorAll(".randomPizzaContainer") and removed dx and newwidth variables out of the for loop since both are not needed. Added switch cases to change pizza pic by percentage instead of pixels.




