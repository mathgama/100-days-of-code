# 100 Days Of Code - Log

### Day 1: October 18, 2021

**Today's Progress**: Created a repo for a new project that will be a basic gallery of graffity photos taken around the world. Also created a basic design structure in plain html and css using bootstrap.

The goal was to set some basic design for the project so I don't have to think about it too much while getting into the React itself. There are some points that I'm still not happy with, like the login button and the submit button that should appear somewhere after the user is logged in. But I guess I should start this way and change those as new ideas come to mind. 

<img src="./img/2021-10-18-template.png" width="70%">

**Link to work:** 
- <https://github.com/mathgama/graffiti-gallery/commit/786bb9857ffa96962e98ac96b72ab5dbfd18d145>


### Day 2: October 19, 2021

**Today's Progress**: Created the NextJS app and started by cleaning up the initial files and adding needed packages like ESLint, Prettier and Bootstrap.

Found one unexpected error because the Bootstrap library doesn't work very well with the server-side rendering provided by NextJS. There is a workaround to solve this ([link](https://stackoverflow.com/questions/67845378/how-can-i-use-bootstrap-5-with-next-js)), but anyway I decided to then use Material-UI instead of Bootstrap, as Material-UI should work "out-of-the-box".

After this initial setup, I started creating the first component of the homepage in a second commit.

**Link to work:** 
- <https://github.com/mathgama/graffiti-gallery/commit/7210be12b6f5076c47083cc206638604d1f75e4b>
- <https://github.com/mathgama/graffiti-gallery/commit/a7f18f587f6d5ea0c7e547b6279dc4d80466ef24>


### Day 3: October 20, 2021

**Today's Progress**: Today I continued developing the UI components needed for the home page. I finished developing the image gallery and the pages now have a header (app bar) and a footer. I'm still using mock data to test the layout as the back-end will be developed in the future.

There are also some components left to do in the upcoming days that do not appear directly in the homepage, like the login page and the page to submit new images.

In the homepage I still need to decide what links I'll include in the navbar, so I left it with no links for now.

![scroll-down](./img/2021-10-20-scroll-down.gif)

**Link to work:** 
- <https://github.com/mathgama/graffiti-gallery/commit/c89e7fcbb0688b83797649658fba792e61c90573>
- <https://github.com/mathgama/graffiti-gallery/commit/1f6e4b9abb05794de71b3ff54c96bd262242a3bd>
- <https://github.com/mathgama/graffiti-gallery/commit/ceff3b59b3aab69cea2687c6d311bf01f904bf27>
- <https://github.com/mathgama/graffiti-gallery/commit/43fd35541b67e92953fc939873388ce21463f653>


### Day 4: October 21, 2021

**Today's Progress**: Struggled a bit trying to find the best way to open the full image when the user clicks a card in the home page.

Need to make sure that the image scales to both "desktop" and "mobile" versions, and that in the mobile version the user will be able to zoom in to see more details. I did commit a first version, but I'm still not satisfied with the result, so I'll need to come back to it in the next days.

**Link to work:** 
- <https://github.com/mathgama/graffiti-gallery/commit/2854537ad9f0d7ec39402b270bb4bbee94891def>


### Day 5: October 22, 2021

**Today's Progress**: Started by removing some unnecessary files from the repo. 

Then created a "submit graffiti" page to enable new images upload. Graffiti data is still quite simple with only 4 fields, but I'll keep it that way until I start using a backend. Then I can enhance it later if needed.

Also made some adjustments to the "full image" view that I began yesterday. Now it is rendering way better than before on mobile devices.

**Link to work:** 
- <https://github.com/mathgama/graffiti-gallery/commit/f7b030c9cc755d5d696e58c979e1e9c5adb2bdb9>
- <https://github.com/mathgama/graffiti-gallery/commit/1cd00e6ddbc2e64a29b21a70784ab280b003a11f>
- <https://github.com/mathgama/graffiti-gallery/commit/0d66ab92c7bca3e91585f4a6c57acd2e406789e8>


### Day 6: October 23, 2021

**Today's Progress**: Decided to use Firebase Cloud Storage module to store the images uploaded by the users.

Had a rough time trying to make it work though. After a long time fiddling with the configuration, I discovered that the official portuguese documentation only have code snippets for the version 8 of the SDK, while I was using version 9. The problem is that the portuguese documentation doesn't even make it clear that there is a new version.

Portuguese docs:

![ptbr-doc](./img/2021-10-23-ptbr-doc.png)

English docs:

![en-doc](./img/2021-10-23-en-doc.png)

After switching to the english documentation I was finally able to get the upload to work!

![image-storage](./img/2021-10-23-storage.png)

**Link to work:** 
- <https://github.com/mathgama/graffiti-gallery/commit/19017977ca00bf17c5d4600babfb3597aed149e1>


### Day 7: October 24, 2021

**Today's Progress**: Enhanced the upload page by adding some feedback to the user that the image is being processed:

![user-feedback](./img/2021-10-24-user-feedback.gif)

Then added some logic to generate an unique filename (using uuid) before sending the image to firebase. This will avoid name collision which can cause accidental overwriting in the storage. This same uuid should be used later on to create an entry in the database.

**Link to work:** 
- <https://github.com/mathgama/graffiti-gallery/commit/69554620949a15f8e5ea9ddde7cfc2ab2358ca31>
- <https://github.com/mathgama/graffiti-gallery/commit/ad6d08c15b247c0d39bb82d37133b55291e0b2d4>


### Day 8: October 25, 2021

**Today's Progress**: Today I started by addind a simple form validation to the "submit graffiti" page. And then, with the image upload working, I started to use firebase to store the rest of the data in a database.

First I spent some time working with the "realtime database" module, and then switched to the "firestore database" module as I discovered that this one is an enhanced version of the aforementioned.

Ended up with the firestore working, but still need to use the read data to render the screen instead of the mock data that I've been using.

**Link to work:** 
- <https://github.com/mathgama/graffiti-gallery/commit/e4abb8064c8502f021cbc004def5e81f54c69322>
- <https://github.com/mathgama/graffiti-gallery/commit/758d2d99cace22485dfb626abd6cd00d691cf98d>


### Day 9: October 26, 2021

**Today's Progress**: First I switched the index page to use the firebase data instead of the mock data I was using before.

Then I started trying to implement pagination to the data fetch. The idea is to make an infinite scroll, fetching a new page everytime the user gets to the end of the scroll. After reading the documentation it seemed pretty easy to do with the firebase SDK, but I ran into some bug in the application react state that I still couldn't fix. And because of this I did not commit this code yet.

**Link to work:** 
- <https://github.com/mathgama/graffiti-gallery/commit/75583d22247369183b2bd0d894c77f91f8291135>


### Day 10: October 27, 2021

**Today's Progress**: Solved the bug I had yesterday and got the infinite scroll to work!

![infinite-scroll](./img/2021-10-27-infinite-scroll.gif)

**Link to work:** 
- <https://github.com/mathgama/graffiti-gallery/commit/75583d22247369183b2bd0d894c77f91f8291135>


### Day 11: October 28, 2021

**Today's Progress**: Started working in the user authentication.

The app is already using the firebase auth module for signing in the user with its Google account. After logging in, the menu on the app bar is changed:

![user-menu](./img/2021-10-28-user-menu.png)

Logout is not implemented yet.

**Link to work:** 
- <https://github.com/mathgama/graffiti-gallery/commit/b60b96366c99fc55daf52b5012be0595eb110f32>


### Day 12: October 29, 2021

**Today's Progress**: First I implemented the user logout that was pending. 

Then I did some refactoring, including the split of the firebase functions, creating different files for each module (firestore, storage and auth). 

Lastly I fixed the user name that was fixed in the image upload and should be using the logged in user info.

**Link to work:** 
- <https://github.com/mathgama/graffiti-gallery/commit/73d884383711e54aa26cff4d376bc3a435baa69f>
- <https://github.com/mathgama/graffiti-gallery/commit/070a6e21759d530100354d917adb46b5a1b6f3e6>
- <https://github.com/mathgama/graffiti-gallery/commit/598c551a9fb4b539db9e2de02705eb6082f744cd>
- <https://github.com/mathgama/graffiti-gallery/commit/4889a84b75aa5cd6f9aebafc9793915c15493eb8>


### Day 13: October 30, 2021

**Today's Progress**: I'm traveling and unfortunately don't have access to my PC. Because of this, I did code but couldn't test any of the features done today.

- Added a route protection for the "submit-graffiti" page, to allow only signed in users to access it;
- Changed the number of images fetched from the firestore per request, to decrease the number of requests;
- Started creating a function to fetch the "featured graffiti" that will appear in the home page.

**Link to work:** 
- <https://github.com/mathgama/graffiti-gallery/commit/868f0e5537b9aabff8d37290f42925a2e657fc21>
- <https://github.com/mathgama/graffiti-gallery/commit/1befadeb24d24b24706b4a93eb5330f5aa6ae4c4>
- <https://github.com/mathgama/graffiti-gallery/commit/b770f3c890248480ed39d28d6897989dac77e766>


### Day 14: October 31, 2021

**Today's Progress**: Fixed the features introduced yesterday and that wasn't tested yet. And then added a link to the home page in the app bar logo.

**Link to work:** 
- <https://github.com/mathgama/graffiti-gallery/commit/3583e96766297524ca0d4a675be38d3f420e98ee>
- <https://github.com/mathgama/graffiti-gallery/commit/89afcaf2a0179518df7529ada18dcaff8743084a>
- <https://github.com/mathgama/graffiti-gallery/commit/9aa3527c0960fd92aab9848391c8e09da9be925d>


### Day 15: November 01, 2021

**Today's Progress**: Created a navbar with a link to the "submit-graffiti" page that should appear only when the user is logged in. It is replaced with a icon to open a drawer when in the mobile version.

Desktop version:

![desktop-navbar](./img/2021-11-01-desktop-navbar.png)

Mobile version:

![mobile-navbar](./img/2021-11-01-mobile-navbar.gif)

**Link to work:** 
- <https://github.com/mathgama/graffiti-gallery/commit/e3e294a9f003ba976fd16d6fb8c274eff838bc04>
- <https://github.com/mathgama/graffiti-gallery/commit/7e690ad4b593876798de8507653fbaa3c3b78702>


### Day 16: November 02, 2021

**Today's Progress**: Updated the project README and fixed some minor bugs for the first release.

Also changed the way I was using environment variables to make it easier to deploy on Vercel. But I'm still having some problems with the deploy that I couldn't figure out yet.

**Link to work:** 
- <https://github.com/mathgama/graffiti-gallery/commit/8a5b3d6b2750dde6c6b8fb700b908b298b8db4d5>
- <https://github.com/mathgama/graffiti-gallery/commit/51197328168e79a25a932549aa9ba11b9af2cf64>
- <https://github.com/mathgama/graffiti-gallery/commit/e2156b1070eb7f78c5bf639eb0b9322ceb2ae14a>


### Day 17: November 03, 2021

**Today's Progress**: It took me some time to figure out the environment variables problem I was having after deploying to Vercel, but with some chanages I was able to fix it.

Now the app is having trouble with permissions while trying to access firebase. It works locally but when deployed to Vercel it doesn't.

**Link to work:** 
- <https://github.com/mathgama/graffiti-gallery/commit/a1a4668f3d919a5fc0f45a92ce629f03d4510d74>


### Day 18: November 04, 2021

**Today's Progress**: Fixed some minor bugs in the app. 

Then I tried to fix the permission error in the Vercel deploy, but I still couldn't figure out what is causing it.

**Link to work:** 
- <https://github.com/mathgama/graffiti-gallery/commit/2d9e473e92eae5f238fc3f59eee7904df7a2ac3b>
- <https://github.com/mathgama/graffiti-gallery/commit/f6ae3a7b41a911067530daadbe3a1ca0759d821f>


### Day 19: November 05, 2021

**Today's Progress**: Decided to take some time doing other things than the Graffiti Gallery app, so I started studying python.

I did lots of tutorials at freeCodeCamp and I hope to start at least a simple project using Python in the near futBack to the graffiti-gallery project, I finally got it to work on Vercel! 

Then I updated the security rules on firebase to protect the storage from:
1. Unauthorized users
2. Files that are not images
3. files that are too big (>5MB)

And with that, graffiti-gallery version 1.0.0 is now released! 🎉ure!

Because I didn't commit anything with Python yet, I decided to create a repo that will be used to build my portfolio. The commit have only a veery simple hello world though, because most of my time was spent studying Python.

**Link to work:** 
- <https://github.com/mathgama/portfolio/commit/68cd14435d337c247b82924e163b2d5eb20b19f3>


### Day 20: November 06, 2021

**Today's Progress**: Continuing the portfolio project, added a navbar and a "welcome" section.

**Link to work:** 
- <https://github.com/mathgama/portfolio/commit/2174fe17eb07621e6ea8af14c911819f94b71d17>


### Day 21: November 07, 2021

**Today's Progress**: Added an "about" section and a "projects" section to the portfolio.

Also fixed the "welcome" section to work better at small devices.

**Link to work:** 
- <https://github.com/mathgama/portfolio/commit/8288967f605599c0aa32316e80e1237dfd143a3d>


### Day 22: November 08, 2021

**Today's Progress**: Added the "backround" section to the portfolio.

**Link to work:** 
- <https://github.com/mathgama/portfolio/commit/78af00b20d74c6481c35205e348794b9224b17e5>


### Day 23: November 09, 2021

**Today's Progress**: Added the "contact" section to the portfolio and fixed some minor bugs.

Now I only need to update the "projects" section with the link the to the actual repositories. But first I need to update those repos to include a better readme.

**Link to work:** 
- <https://github.com/mathgama/portfolio/commit/487d4de820dd713f95a9d2c7bdddaf12207d3869>
- <https://github.com/mathgama/portfolio/commit/01ef5b5e38e28c80dc5cb6424b21a657b684f974>


### Day 24: November 10, 2021

**Today's Progress**: Back to the graffiti-gallery project, I finally got it to work on Vercel! 

Then I updated the security rules on firebase to protect the storage from:
1. Unauthorized users
2. Files that are not images
3. files that are too big (>5MB)

And with that, graffiti-gallery version 1.0.0 is now released! 🎉

**Link to work:** 
- <https://github.com/mathgama/graffiti-gallery/commit/85b32f4854b1be99da20d80a9afb92775d9e499c>
- <https://github.com/mathgama/graffiti-gallery/commit/eb5c6b3bb59435c569da4033da3dde1ab1bd7b3a>


### Day 25: November 11, 2021

**Today's Progress**: Solved some minor bugs in the graffiti-gallery project.

Then went back to an old project called spotify-featured-playlists and updated its readme while also fixing some minor bugs and doing some cleanup on the repository.

The goal is to have some minimum documentation on at least some projects to be able to include them in my portfolio.

**Link to work:** 
- <https://github.com/mathgama/graffiti-gallery/commit/8264a4fe6c537e532fad5f843672eb325a642268>
- <https://github.com/mathgama/graffiti-gallery/commit/21eb543e62ef18f15f98cbb24a763442f67a75b5>
- <https://github.com/mathgama/spotify-featured-playlists/commit/fc9f381c37d655a1a49e601fae9433129794296f>
- <https://github.com/mathgama/spotify-featured-playlists/commit/436dece7359682b5459cdf46c951a5c48b5e8fb6>
- <https://github.com/mathgama/spotify-featured-playlists/commit/e04785898c0a254cea8b802ba76380bdde51ac38>


### Day 26: November 12, 2021

**Today's Progress**: Worked at my portfolio doing some minor bug/typo fixes and updating the "projects" section with the link to the github repos.

Changed the repository name to "mathgama.github.io" to be able to use the GitHub Pages feature, and then spent some time registering and configuring domains for it.

The portfolio is now available at [https://matheusgama.com/](https://matheusgama.com/)!

**Link to work:** 
- <https://github.com/mathgama/mathgama.github.io/commit/aefea022ea7e63ba8a55b56bc3b6643be398d795>
- <https://github.com/mathgama/mathgama.github.io/commit/709730dfb1dbaf48fa9d4126ccd9045d3838e5ee>
- <https://github.com/mathgama/mathgama.github.io/commit/b7812abaaf1115185a4ff6856b5b0852cea463d1>


### Day 27: November 13, 2021

**Today's Progress**: Started a new project called "sudoku-solver". First step is to make a sudoku game using Python's library PyGame. 

Started by learning about virtual environments and creating the repository. Then implemented the grid draw along with a initial board state that is fetched from the [Sugoku](https://github.com/bertoort/sugoku) API.

![sudoku-board](./img/2021-11-13-sudoku-board.png)

**Link to work:** 
- <https://github.com/mathgama/sudoku-solver/commit/356a02eaf70a32e861158e4fd9b2df06c23d9d4f>
- <https://github.com/mathgama/sudoku-solver/commit/c96e7a6998e18dbd26a9e18df2c73f0db6d1cbd1>
- <https://github.com/mathgama/sudoku-solver/commit/aa50392a422498adc2d12db4d73d463c6bab7eba>


### Day 28: November 14, 2021

**Today's Progress**: Refactored the program to use classes and did some tweaks on the board "responsiveness". One of the things I wanted was that the program should be able to work with variable board/cell sizes.

Then implemented the "cell selection" feature. The board will highlight the clicked cell so that the user can type the number in.

**Link to work:** 
- <https://github.com/mathgama/sudoku-solver/commit/356a02eaf70a32e861158e4fd9b2df06c23d9d4f>
- <https://github.com/mathgama/sudoku-solver/commit/c96e7a6998e18dbd26a9e18df2c73f0db6d1cbd1>
- <https://github.com/mathgama/sudoku-solver/commit/aa50392a422498adc2d12db4d73d463c6bab7eba>


### Day 29: November 15, 2021

**Today's Progress**: Added user input and validation to see if the input is valid according to the game rules. Also added the possibility of moving the cell selection with the arrow keys.

With this, the game is now in a playable state! I feel like there's a lot of room for optimization, but I won't dive too much into it since it is not my goal right now.

<img src="./img/2021-11-15-sudoku-validation.gif" width="355px">

Next steps should be:
1. Creating an algorithm for self-solving;
2. Image recognition to add the possibility of reading a sudoku grid from a photo instead of using the API.

**Link to work:** 
- <https://github.com/mathgama/sudoku-solver/commit/6feb949cf9305d67d022755af009b0115c70ed84>
- <https://github.com/mathgama/sudoku-solver/commit/9a08c96114027cc4cbe08bdfec8da5630da6b9a8>
- <https://github.com/mathgama/sudoku-solver/commit/17fe31e54d0c3413c33344936222efc958d62b50>


### Day 30: November 16, 2021

**Today's Progress**: First I fixed a bug in the function used to validate the user input. 

Then I created a function to solve the board automatically using recursion! I am pretty happy with the result since I haven't looked for solutions from other developers before doing my own. The only thing I knew is that recursion was the most adopted solution (judging by the title of the videos on Youtube title at least), than I tried to create my own algorithm based on that.

It usually gets to the solution pretty fast:

![sudoku-time-to-solve](./img/2021-11-16-sudoku-time-to-solve.png)

**Link to work:** 
- <https://github.com/mathgama/sudoku-solver/commit/5f7d344c7736a93f218466cbe750f2c7d5cc1567>


### Day 31: November 17, 2021

**Today's Progress**: Started doing some tests with OpenCV to recognize a sudoku board from a photo/image. Found an awesome [video](https://www.youtube.com/watch?v=qOXDoYUgNlU) on Youtube that should help me alot.

With today's code I was able to turn this original image:

<img src="./img/2021-11-17-sudoku-orig-image.png" width="280px" />

Into this image, cropping only the sudoku board and discarding the rest:

<img src="./img/2021-11-17-sudoku-cropped-board.png" width="300px" />

**Link to work:** 
- <https://github.com/mathgama/sudoku-solver/commit/cc718bbeaaf4507b18a6839c2ae7a3f430e543f7>


### Day 32: November 18, 2021

**Today's Progress**: Chopped the whole board image into 81 smaller images containing each one of the cells of the board. 

<img src="./img/2021-11-18-sudoku-cell-image.png" width="280px" />

Then used Tesseract to recgonize the value of each cell and store them in a array. Now I only need to format the data in the way that the GUI is expecting it to be.

For the image I was using in the tests, the character recognition worked pretty well. In the next days I'll try to test with actual photos from my cell phone and see how it goes.

**Link to work:** 
- <https://github.com/mathgama/sudoku-solver/commit/83f3d58d627e6dfb7a52ef2276fce191e1aa9db6>


### Day 33: November 19, 2021

**Today's Progress**: Now both modules ("game GUI" and "image recognition") are working together!

The user should now be able to pass an argument when starting the game to load the initial state from an image:

```
python3 game.py -i <image_path>
```

When started without the "-i" argument, the game will fetch an initial board state from the Sugoku API as described in previous days.

Original image:

<img src="./img/2021-11-17-sudoku-orig-image.png" width="280px" />

Game GUI:

<img src="./img/2021-11-19-sudoku-board-recognized.png" width="280px" />

After using the auto-solve function:

<img src="./img/2021-11-19-sudoku-board-solved.png" width="280px" />

**Link to work:** 
- <https://github.com/mathgama/sudoku-solver/commit/9caba1f88dbc8bf8709eebe2964d93fed1593fb9>
- <https://github.com/mathgama/sudoku-solver/commit/82de42f53600aa1962ee9435c346c74e4dbfd2bd>


### Day 34: November 20, 2021

**Today's Progress**: Started a new Python project called "racing-cars".

The idea is to build a simple racing game where the user should be able to race a car around a track.

I'll probably follow this [video](https://www.youtube.com/watch?v=L3ktUWfAMPg) for most of the game itself, but my end goal really is to modify the game a little and to implement neural networks at the end to see if the computer can learn to race the track by itself!

**Link to work:** 
- <https://github.com/mathgama/racing-cars/commit/1301eec09b60e3c6f1b28cb98741cc5958ac45b8>


### Day 35: November 21, 2021

**Today's Progress**: Added a "car" class and some basic functions, including the drawing of the car in the screen.

Also did some minor refactoring in the "sudoku-solver" project.

**Link to work:** 
- <https://github.com/mathgama/racing-cars/commit/da6c807ac171da16dee0f7beb022f6112f129fbf>
- <https://github.com/mathgama/sudoku-solver/commit/e2446d47e86c18654a32b3111910bd1202f4c0f6>


### Day 36: November 22, 2021

**Today's Progress**: Added car rotation and car movement. 

Now the car can already be driven around the track, but it still lacks collision detection:

<img src="./img/2021-11-22-car-movement.gif" width="350px" />

**Link to work:** 
- <https://github.com/mathgama/racing-cars/commit/e6184ce2048957a43fdcaa24f06cf3aa98695b49>


### Day 37: November 23, 2021

**Today's Progress**: Added collision detection and car deceleration when not pressing "W (forward)".

Now I consider the game to be playable, with the user being able to move around the track and not being able to pass through the track borders. It still lacks some features, but I think that in the current state I will be able to start working on the machine learning.

**Link to work:** 
- <https://github.com/mathgama/racing-cars/commit/7e508b71458d28dbf4f230d31356e83121125f10>
- <https://github.com/mathgama/racing-cars/commit/416511feab7e978f76ac18efd67b22412bd1b2ee>


### Day 38: November 24, 2021

**Today's Progress**: Added some sensors to the car that should measure the distance to the closest obstacles.

Started by adding 3 sensors, one in the front (labelled "f"), and one in each side of the car (labelled "r" and "l"):

![car-sensors](./img/2021-11-24-car-sensors.png)

The last line in the terminal corresponds to the distances measured in the above image:

![car-sensors-values](./img/2021-11-24-car-sensors-values.png)

Every time the car moves or turns, the distances are updated.

Those sensors will be used by the neural network in the future, and I'll probably add 2 more sensors in between those 3, for it to be more accurate.

**Link to work:** 
- <https://github.com/mathgama/racing-cars/commit/5ff55d4306115b7013d3da3dac751b98a5a0a9ef>


### Day 39: November 25, 2021

**Today's Progress**: Started by doing some refactoring in the car class to make it more easier to instantiate.

Then added 2 more sensors to the car, making it 5 total ("left", "left-front", "front", "right-front" and "right").

And lastly, added a way to measure the score based on how far the car has moved from the starting point. Used a technique called "wavefront propagation" to determine the score of each point of the track. Pretty happy with it since I wrote the algorithm myself without looking for any code prior to it.

**Link to work:** 
- <https://github.com/mathgama/racing-cars/commit/16774a7993aec41bb26cccc35ebb0aa0d6dbdfd6>
- <https://github.com/mathgama/racing-cars/commit/4b6f8cc2ede5bb264924bd5275b523d4d7e60095>
- <https://github.com/mathgama/racing-cars/commit/a9490729e162b416212460032bde5916abdcecff>


### Day 40: November 26, 2021

**Today's Progress**: Added a finish line to the track and updated the collision points to account for it.

**Link to work:** 
- <https://github.com/mathgama/racing-cars/commit/dee399c41ac738be89a05fa89ab25f240e4d8f01>


### Day 41: November 27, 2021

**Today's Progress**: After doing some research on neural networks, I found out that refactoring the main file would make it easier to implement in the future.

Started doing it but wasn't able to get the game to a "playable" state, commited anyway just to show some progress.

**Link to work:** 
- <https://github.com/mathgama/racing-cars/commit/0d18767c6b4541e27dafe5ce427b4cd9b14815ff>


### Day 42: November 28, 2021

**Today's Progress**: Finished the refactoring started yesterday. I had some trouble to account for multiple key strokes at the same time after the refactoring but I was able to solve it.

Now there's a "game" class insted of having many things in the game loop like before. This should ease the neural network implementation.

**Link to work:** 
- <https://github.com/mathgama/racing-cars/commit/c6ff2fca512c3f61c14c5ab2dc62a97df80ffec4>
- <https://github.com/mathgama/racing-cars/commit/6f1f9669fed864404855d52580bc5160e7373c26>


### Day 43: November 29, 2021

**Today's Progress**: I spent some time learning a bit more about neural networks, so not a lot of code was commited.

I created an "agent" class that should contain the steps needed for the AI to train on the game. In this class I started by implementing a method that should be responsible for structuring the game actual state (the car speed, angle and it's sensors values).

This state will be used by the neural network to determine the car next actions.

**Link to work:** 
- <https://github.com/mathgama/racing-cars/commit/0b4bc764a053aa583a8f29c409fa014753f76730>


### Day 44: November 30, 2021

**Today's Progress**: Once again, not a lot of code commited, but still had some advance in the "agent" class. 

I also had to study a bit about pytorch and tensors to understand it better before continuing with the neural network implementation.

**Link to work:** 
- <https://github.com/mathgama/racing-cars/commit/c56c8ab8a97a1204fcf3bc568f3989cd5300ffd6>


### Day 45: December 01, 2021

**Today's Progress**: I was able to finish the model and the trainer classes, but I still got some errors because in this game the user should be able to perform multiple actions at once (eg. accelerate and turn at the same time) and the model isn't prepared for that.

**Link to work:** 
- <https://github.com/mathgama/racing-cars/commit/96eddb348a571e1c7521f237df13daddb79a623b>


### Day 46: December 02, 2021

**Today's Progress**: Changed the way that the game handles user input to make it easier for the model to predict the next action given that 2 commands at the same time should be possible.

I was finally able to run the IA and see the car driving by itself! But I noticed that after approximately 100 games the IA was getting stuck at the start line insted of moving forward, even with a negative reward for it.

**Link to work:** 
- <https://github.com/mathgama/racing-cars/commit/b29fb59dafc8c94bb064d31c30e43fd540c2b58c>


### Day 47: December 03, 2021

**Today's Progress**: I started messing a little with the IA parameters to see if the learning could be improved, but didn't have too much progress to be honest. The car is still getting stuck after some time training.

**Link to work:** 
- <https://github.com/mathgama/racing-cars/commit/b29fb59dafc8c94bb064d31c30e43fd540c2b58c>


### Day 48: December 04, 2021

**Today's Progress**: Still changing the IA parameters, but this time I had some progress.

After 500 games, the car was able to score 3952 points, which means running through the entire track!

![car-record-score](./img/2021-12-04-car-record-score.png)

But for some reason, it was not able to keep doing that consistently 🙁. Anyway, pretty happy that some progress was made!

**Link to work:** 
- <https://github.com/mathgama/racing-cars/commit/b29fb59dafc8c94bb064d31c30e43fd540c2b58c>


### Day 49: December 05, 2021

**Today's Progress**: I decided to take a break from the "racing-cars" project and start on two "advent of code" challenges:

- [Dev Advent Calendar](https://github.com/devadvent/readme/) - Which I'll refer to as DevAdvent from now on
- [Advent of Code 2021](https://adventofcode.com/2021/about) - Which I'll refer to as AoC from now on

The "Dev Advent Calendar" is already on day 5, so I began by submitting this one. It uses Github Classroom to create a private repository, so I won't be able to link the commits for this one.

For the "Advent of Code 2021" I decided to start on day 1. In the next couple days I'll try to submit multiple days to get me up-to-date.

**Link to work:** 
- <https://github.com/mathgama/advent-of-code-2021/commit/56b860b4cf81d9284bfaac5b6c7b00658ab13554>


### Day 50: December 06, 2021

**Today's Progress**: Continuing with the code advents:

- [Puzzle 06](https://github.com/devadvent/puzzle-6) from the [Dev Advent Calendar](https://github.com/devadvent/readme/)
- [Day 02](https://adventofcode.com/2021/day/2) from the [Advent of Code 2021](https://adventofcode.com/2021/about)
- [Day 03](https://adventofcode.com/2021/day/3) from the [Advent of Code 2021](https://adventofcode.com/2021/about)

**Link to work:** 
- <https://github.com/mathgama/advent-of-code-2021/commit/ef19039fa0b5bb5c711cf90e9732c8e0b9b15852>
- <https://github.com/mathgama/advent-of-code-2021/commit/8d8fb6baa27a121d0855d837e6fe2bf855ff8c02>


### Day 51: December 07, 2021

**Today's Progress**: Continuing with the code advents:

- [Puzzle 07](https://github.com/devadvent/puzzle-7) from the [Dev Advent Calendar](https://github.com/devadvent/readme/)
- [Day 04](https://adventofcode.com/2021/day/4) from the [Advent of Code 2021](https://adventofcode.com/2021/about)

Day 04 from the AoC isn't complete though. It still isn't giving the proper result for the second part of the challenge.

**Link to work:** 
- <https://github.com/mathgama/advent-of-code-2021/commit/eaa221aa9152dd29d9b72d53577d6fd63f5c7889>


### Day 52: December 08, 2021

**Today's Progress**: Continuing with the code advents:

- [Puzzle 08](https://github.com/devadvent/puzzle-8) from the [Dev Advent Calendar](https://github.com/devadvent/readme/)

Unfortunately I didn't have enough time to go on with the AoC, since the puzzle 08 from the DevAdvent took me more time than I expected.

**Link to work:** 
- Commits to private repository :(


### Day 53: December 09, 2021

**Today's Progress**: Continuing with the code advents:

- [Puzzle 09](https://github.com/devadvent/puzzle-9) from the [Dev Advent Calendar](https://github.com/devadvent/readme/)
- [Day 04](https://adventofcode.com/2021/day/4) from the [Advent of Code 2021](https://adventofcode.com/2021/about)

Puzzle 09 from DevAdvent was pretty easy since I already had to use binary conversion in previous days of the AoC! 

Then I was able to find the bug in the day 04 of the AoC and start to solve day 05, but couldn't get to the right response of the first part yet.

**Link to work:** 
- <https://github.com/mathgama/advent-of-code-2021/commit/9bef9be54b4bbce492e3113912213ab9756738d9>
- <https://github.com/mathgama/advent-of-code-2021/commit/61cdb59774720c9a80d1b118e0dc261b27c5891c>


### Day 54: December 10, 2021

**Today's Progress**: Continuing with the code advents:

- [Puzzle 10](https://github.com/devadvent/puzzle-10) from the [Dev Advent Calendar](https://github.com/devadvent/readme/)
- [Day 05](https://adventofcode.com/2021/day/5) from the [Advent of Code 2021](https://adventofcode.com/2021/about)

**Link to work:** 
- <https://github.com/mathgama/advent-of-code-2021/commit/b1619092230fba057dfcfeb7ec8b729b03e90377>
- <https://github.com/mathgama/advent-of-code-2021/commit/e10d89856adf5528cd20495718ba6f5f0a5782f8>


### Day 55: December 11, 2021

**Today's Progress**: No code advents today because I did participate on the [SAP Labs Online Contest](https://www.beecrowd.com.br/judge/en/contests/view/628).

Turned out it was wayy more difficult than I was expecting. I'll definitely try to solve more problems on beecrowd to get more practice and then try my skills again on another contest.

**Link to work:** 
- <https://github.com/mathgama/sap-labs-contest/commit/4978d1a171cbdeb6836ed298256c5d93e32354c6>
- <https://github.com/mathgama/sap-labs-contest/commit/cbf683a5029f2da23fc902497b145a9fd171c8b3>


### Day 56: December 12, 2021

**Today's Progress**: Back to the code advents:

- [Day 06](https://adventofcode.com/2021/day/6) from the [Advent of Code 2021](https://adventofcode.com/2021/about)

I did begin day 07, but I still need to solve the second part of it.

**Link to work:** 
- <https://github.com/mathgama/advent-of-code-2021/commit/d889dfad9f06a8ae7f27a34d3134c0365713405e>
- <https://github.com/mathgama/advent-of-code-2021/commit/49bdaea0af781e053ec7ac2f8dae1a0d353f6fe4>
- <https://github.com/mathgama/advent-of-code-2021/commit/6d3d56a0a9124db2d39d4072c84dbe7c087cb011>


### Day 57: December 13, 2021

**Today's Progress**: Continuing with the code advents:

- [Puzzle 13](https://github.com/devadvent/puzzle-13) from the [Dev Advent Calendar](https://github.com/devadvent/readme/)
- [Day 07](https://adventofcode.com/2021/day/7) from the [Advent of Code 2021](https://adventofcode.com/2021/about)

Also finished the first part of the AoC - Day 08.

**Link to work:** 
- <https://github.com/mathgama/advent-of-code-2021/commit/81bf941801766b1d5f5e890268650a014e0a8ff7>
- <https://github.com/mathgama/advent-of-code-2021/commit/af1dbc7238702ff0244a582830f85ffb7ec99733>


### Day 58: December 14, 2021

**Today's Progress**: Continuing with the code advents:

- [Puzzle 14](https://github.com/devadvent/puzzle-14) from the [Dev Advent Calendar](https://github.com/devadvent/readme/)
- [Day 08](https://adventofcode.com/2021/day/8) from the [Advent of Code 2021](https://adventofcode.com/2021/about)

**Link to work:** 
- <https://github.com/mathgama/advent-of-code-2021/commit/be3e8b01aadd41ff01670fe10ee61563ddbaab9f>


### Day 59: December 15, 2021

**Today's Progress**: Continuing with the code advents:

- [Puzzle 15](https://github.com/devadvent/puzzle-15) from the [Dev Advent Calendar](https://github.com/devadvent/readme/)

I also started Day 09 of the AoC but couldn't finish the second part of it.

**Link to work:** 
- <https://github.com/mathgama/advent-of-code-2021/commit/a46f7403baf21c8b360603282157898776d1e18a>


### Day 60: December 16, 2021

**Today's Progress**: Continuing with the code advents:

- [Puzzle 16](https://github.com/devadvent/puzzle-16) from the [Dev Advent Calendar](https://github.com/devadvent/readme/)
- [Day 09](https://adventofcode.com/2021/day/9) from the [Advent of Code 2021](https://adventofcode.com/2021/about)

I also started Day 10 of the AoC but couldn't finish the second part of it.

**Link to work:** 
- <https://github.com/mathgama/advent-of-code-2021/commit/918e3a97edae708aa2e420812c6c727863a5c8d8>
- <https://github.com/mathgama/advent-of-code-2021/commit/c6dfe425c10d6f245cce43b44d82728dd26a934f>


### Day 61: December 17, 2021

**Today's Progress**: Continuing with the code advents:

- [Puzzle 17](https://github.com/devadvent/puzzle-17) from the [Dev Advent Calendar](https://github.com/devadvent/readme/)
- [Day 10](https://adventofcode.com/2021/day/10) from the [Advent of Code 2021](https://adventofcode.com/2021/about)

**Link to work:** 
- <https://github.com/mathgama/advent-of-code-2021/commit/2dfc0d5d8b40faa9f02f267337e854badf96376b>


### Day 62: December 18, 2021

**Today's Progress**: Continuing with the code advents:

- [Puzzle 18](https://github.com/devadvent/puzzle-18) from the [Dev Advent Calendar](https://github.com/devadvent/readme/)

Also decided to try something new, so I started coding new features for a [Discord bot](https://github.com/tresende/discord-bot) that is already used in a server that I have with my friends. So I spent some time understanding what is already built, just so I can start to develop a new feature in the upcoming days.

**Link to work:** 
- Commit to private repository


### Day 63: December 19, 2021

**Today's Progress**: I started creating a new feature for the Discord bot and the goal was to reply to specific command with a image containing some economic indicators from our country (Brazil).

I was able to make it work locally. The bot navigates to a website and takes a screenshot that will be used in the reply.

But I'm still not happy with the way I added this to the already existing code. The existing code isn't ready to generate responses asynchronously, which is the case here, and I had a hard time trying to do this on Typescript.

For this reason, I did not commit any of this code yet.

![discord-bot-reply](./img/2021-12-20-discord-bot-reply.png)

**Link to work:** 
- No commits :(


### Day 64: December 20, 2021

**Today's Progress**: I still tried to solve the async problems from yesterday, but no luck.

To avoid another day without commits, I switched to a different (and easier) feature that I was intending to do. And althought it is pretty simple, I'm happy to finish this after 2 days stuck with the first one!

**Link to work:** 
- <https://github.com/tresende/discord-bot/commit/e040bfb5b250cdc553cf4f6b3da70292bb3aeaec>


### Day 65: December 21, 2021

**Today's Progress**: I created another feature for the discord bot that should reply to messages containing certain words with a random gif from a list of pre configured links.

The sets of words and corresponding gifs are customizable via the settings.json file.

Also set the chance will reply a gif only 50% of the time (considering there's a word match), to avoid spamming.

Besides that, did some other minor fixes on the bot.

**Link to work:** 
- <https://github.com/tresende/discord-bot/commit/6863f5d718b2abddfe51f8681fffb5074c0b5cb4>
- <https://github.com/tresende/discord-bot/commit/c48d99f755312470c8b9e6f52308d8632bad2278>
- <https://github.com/tresende/discord-bot/commit/d29854fc41da087e0a15da899c92cf87bc58fdef>
- <https://github.com/tresende/discord-bot/commit/2429aaf819ff2d9a9bedb927d99a6683fb807c37>


### Day 66: December 22, 2021

**Today's Progress**: Back to the code advents:

- [Puzzle 22](https://github.com/devadvent/puzzle-22) from the [Dev Advent Calendar](https://github.com/devadvent/readme/)

I also started day 11 of the [Advent of Code 2021](https://adventofcode.com/2021/about), but could only finish the first part of it (struggled a bit with it as it was not that easy to debug).

**Link to work:** 
- <https://github.com/mathgama/advent-of-code-2021/commit/0f313e6b788d7d62c581e559f78e1ee75c3fae1a>


### Day 67: December 23, 2021

**Today's Progress**: Continuing with the code advents:

- [Puzzle 23](https://github.com/devadvent/puzzle-23) from the [Dev Advent Calendar](https://github.com/devadvent/readme/)
- [Day 11](https://adventofcode.com/2021/day/11) from the [Advent of Code 2021](https://adventofcode.com/2021/about)

**Link to work:** 
- <https://github.com/mathgama/advent-of-code-2021/commit/701a4a54c635ff31e336a289960aaa5edfba1f47>


### Day 68: December 24, 2021

**Today's Progress**: Continuing with the code advents:

I started solving day 12 of the Advent of Code 2021, but struggled with it a bit and couldn't get the recursion function to work just right.

**Link to work:** 
- <https://github.com/mathgama/advent-of-code-2021/commit/062818eaf521a9ad3b9d967049907c06c3abecb8>


### Day 69: December 25, 2021

**Today's Progress**: Yesterday, as soon as I turned off my PC and went to celebrate Christmas with my family, I started to have some cool insights on how to solve the problem. So today it took like 2 minutes to finish solving the first part with those ideas!

Then I started trying to solve part 2, but found it pretty difficult as well. The algorithm is actually able to solve smaller test cases, but in the biggest one it just keep on processing and never finishes. It probably needs some optimization, or change the approach (but I hope it doesn't get to this point).

**Link to work:** 
- <https://github.com/mathgama/advent-of-code-2021/commit/cf209ad3e6a25a2ecb73a5c1ac62c7e62d3b9873>
- <https://github.com/mathgama/advent-of-code-2021/commit/bcb8fcc6d96805091a9f86e12df7ab64d0334cd8>


### Day 70: December 26, 2021

**Today's Progress**: I still tried to solve part 2 of day 12, but wasn't able to make it work. The commit itself was very small, but did lots of debugging and testing trying different things.

**Link to work:** 
- <https://github.com/mathgama/advent-of-code-2021/commit/83dc79e7f5dc83f18c40ee549151ee501bf9803b>


### Day 71: December 27, 2021

**Today's Progress**: Continuing with the code advents:

- [Day 13](https://adventofcode.com/2021/day/13) from the [Advent of Code 2021](https://adventofcode.com/2021/about)

**Link to work:** 
- <https://github.com/mathgama/advent-of-code-2021/commit/7e51b6156d786ebdafe963f20b9cb766b115d39b>
- <https://github.com/mathgama/advent-of-code-2021/commit/79f7c1569b3f505bf6153b1f078807d7f94d0fe1>


### Day 72: December 28, 2021

**Today's Progress**: Continuing with the code advents:

I was able to solve only the first part of the day 14, after having to spend some time trying to understand better how the Array.length works in Javascript. It doesn't count exactly how many elements the array haves:

![array-length](./img/2021-12-28-array-length.png)

**Link to work:** 
- <https://github.com/mathgama/advent-of-code-2021/commit/6b0586e79548bcb8aa18715113116952eb53e800>


### Day 74: December 29, 2021

**Today's Progress**: Continuing with the code advents:

- [Day 14](https://adventofcode.com/2021/day/14) from the [Advent of Code 2021](https://adventofcode.com/2021/about)

**Link to work:** 
- <https://github.com/mathgama/advent-of-code-2021/commit/d64e184a18000be037f685aa605b8d929440e879>


### Day 75: December 30, 2021

**Today's Progress**: Continuing with the code advents:

I started day 15, but with it needed shortest path solving to be done. As I noticed I'm having difficulty with shortest path problem (like in day 12), I decided to study the Djikstra Algorithm before trying to solve this problem.

After studying it, I began implementing it in my project. But didn't get to finish the part 1 of the challenge yet.

**Link to work:** 
- <https://github.com/mathgama/advent-of-code-2021/commit/15ad386fe9d63b67a440efb94d408f1c4e85f6e1>


### Day 76: December 31, 2021

**Today's Progress**: Continuing with the code advents:

Part 1 of day 15 that I started yesterday was closer to ready than I expected, it only needed small changes. So I was able to fix it and finish the 2nd part of the problem as well!

- [Day 15](https://adventofcode.com/2021/day/15) from the [Advent of Code 2021](https://adventofcode.com/2021/about)

**Link to work:** 
- <https://github.com/mathgama/advent-of-code-2021/commit/38e558cfdd243437954594a8ed11292ce9ec4cf3>
- <https://github.com/mathgama/advent-of-code-2021/commit/e821d9cc20747299b5b96b9bb2321ebf1905ec1a>


### Day 77: January 01, 2022

**Today's Progress**: Continuing with the code advents:

I started day 16, but I found the problem description a bit complicated at first. After failing with my first implementation because I misunderstood the problem, I restarted and was able to finish the 1st part of the problem!

**Link to work:** 
- <https://github.com/mathgama/advent-of-code-2021/commit/bfe65c608691fb6aa1a63fe3271a5f9496cb4ab8>
- <https://github.com/mathgama/advent-of-code-2021/commit/8192521738a0659a2a07b459721a75442fa64a15>


### Day 78: January 02, 2022

**Today's Progress**: Continuing with the code advents:

- [Day 16](https://adventofcode.com/2021/day/16) from the [Advent of Code 2021](https://adventofcode.com/2021/about)

**Link to work:** 
- <https://github.com/mathgama/advent-of-code-2021/commit/b4871f2cf9787ac07ac4edb3abea0bc59e346410>


### Day 79: January 03, 2022

**Today's Progress**: Continuing with the code advents:

Today I was able to finish part one of the day 17. Pretty happy with the math formula I developed to calculate the Y position of the object considering its acceleration.

**Link to work:** 
- <https://github.com/mathgama/advent-of-code-2021/commit/aa0fb88786b63c15399e3622205e5241d172c08c>


### Day 80: January 04, 2022

**Today's Progress**: Continuing with the code advents:

- [Day 17](https://adventofcode.com/2021/day/17) from the [Advent of Code 2021](https://adventofcode.com/2021/about)

**Link to work:** 
- <https://github.com/mathgama/advent-of-code-2021/commit/1f8882c9c9cc66ff0ecee3721bd912598821f3f2>
- <https://github.com/mathgama/advent-of-code-2021/commit/46978de167b3b4fbff5f187664e6e9724033234f>


### Day 81: January 05, 2022

**Today's Progress**: Continuing with the code advents:

I started day 18 but couldn't do much, not even finished the first part of it. At first I thought I was just out of focus, but after I decided to search reddit to see if I could at least get some hint on how to start solving this problem, I noticed from others opinion that this was one of hardest problems to solve this year.

**Link to work:** 
- <https://github.com/mathgama/advent-of-code-2021/commit/e0d126175e377c76c107b31f22f0b985d2decf06>


### Day 82: January 06, 2022

**Today's Progress**: Continuing with the code advents:

After struggling a bit with it yesterday, I was able to finish part 1 of day 18. Just by changing the data structure it became way, way easier.

**Link to work:** 
- <https://github.com/mathgama/advent-of-code-2021/commit/8cd6e034da74b64060db11ad0296e85214b06c52>
- <https://github.com/mathgama/advent-of-code-2021/commit/c7c35c262db436619692323cda60e7632418a667>


### Day 83: January 07, 2022

**Today's Progress**: Continuing with the code advents:

- [Day 18](https://adventofcode.com/2021/day/18) from the [Advent of Code 2021](https://adventofcode.com/2021/about)

I also started day 19, since part 2 of day 18 was pretty easy. But I found day 19 to be pretty difficult and wasn't able to do much.

**Link to work:** 
- <https://github.com/mathgama/advent-of-code-2021/commit/6128bc80cdf5a249ffc477a2c3b6bffba4a54271>
- <https://github.com/mathgama/advent-of-code-2021/commit/7a64de436ae0eb8cfc2666e52dcc3f3eaea4a6ab>


### Day 84: January 08, 2022

**Today's Progress**: Continuing with the code advents:

I still tried to solve day 19 but as I saw I was wasn't making too much progress, I skipped it and finished day 20 part 1.

**Link to work:** 
- <https://github.com/mathgama/advent-of-code-2021/commit/bfff4741a7e62daadcb5fbf8788ec31209baca50>


### Day 85: January 09, 2022

**Today's Progress**: Continuing with the code advents:

- [Day 20](https://adventofcode.com/2021/day/20) from the [Advent of Code 2021](https://adventofcode.com/2021/about)

**Link to work:** 
- <https://github.com/mathgama/advent-of-code-2021/commit/5dedae1c173396f7bf973cb9c55867eeeb1fa64e>


### Day 86: January 10, 2022

**Today's Progress**: Continuing with the code advents:

Today I was able to finish both parts of day 21!

- [Day 21](https://adventofcode.com/2021/day/21) from the [Advent of Code 2021](https://adventofcode.com/2021/about)

**Link to work:** 
- <https://github.com/mathgama/advent-of-code-2021/commit/16f2744503a2f334c57081da103006a40666c823>
- <https://github.com/mathgama/advent-of-code-2021/commit/0b12bb34a6eccf7e3b6a23afe1a0ec81b1b9746d>


### Day 87: January 11, 2022

**Today's Progress**: Continuing with the code advents:

I finished part 1 of day 22.

**Link to work:** 
- <https://github.com/mathgama/advent-of-code-2021/commit/13e61759d9b15232ad7c56920456be9c51702dcd>


### Day 88: January 12, 2022

**Today's Progress**: Continuing with the code advents:

I started trying to solve part 2 of day 22, but couldn't make too much progress. It needs some knowledge on how to optimize an algorithm to intersect cubes in an 3d array and I'm not into it.

So I decided to skip it and start day 23. After reading the problem, I noticed it was so much easier to solve the problem manually instead of developing an algorithm, so I did this and I was able to get the star for part 1.

But anyway, I decided to try and solve the problem using an algorithm (after all, the challenge is called "100 days of code" for a reason). So I started developing the algorith but wasn't able to finish it.

**Link to work:** 
- <https://github.com/mathgama/advent-of-code-2021/commit/8a64a015641c0d6e0421a6cf5277a90435688d49>


### Day 89: January 13, 2022

**Today's Progress**: Continuing with the code advents:

I'm still trying to finish the algorithm for the day 23, but couldn't do it yet. Apparently it can be done using Djikstra, which I recently learned for day 15. So I managed to code some rules to store the problem state, and check for possible moves and it's costs.

**Link to work:** 
- <https://github.com/mathgama/advent-of-code-2021/commit/cc9a6209065e1729e403d9dee8ab807b5cb7b70c>


### Day 90: January 14, 2022

**Today's Progress**: Continuing with the code advents:

Still on day 23, the code I wrote yesterday still needed some fixes and some more rules to represent the problem accordingly.

**Link to work:** 
- <https://github.com/mathgama/advent-of-code-2021/commit/5899154bfbdba01293a9c4e196e23a7c30202609>


### Day 91: January 15, 2022

**Today's Progress**: Continuing with the code advents:

Still on day 23, today I was able to start implementing the Djikstra algorithm. After doing it, I tried optimizing a bit because it was pretty slow at first.

And then I was pretty happy to get to the correct result for the example input! But the sad part is, it didn't work for the real input. It was really really close to the minimum "path", but not quite it yet. I tried debugging it a bit but still didn't find the reason for the error.

**Link to work:** 
- <https://github.com/mathgama/advent-of-code-2021/commit/a8cce349bd8406ccc27fa6822f353b4f47c36472>


### Day 92: January 16, 2022

**Today's Progress**: Continuing with the code advents:

Lots of debugging to try and some minor changes did the trick! Part 1 of day 23 solved.

**Link to work:** 
- <https://github.com/mathgama/advent-of-code-2021/commit/64adb3f6cbefdaff5808320da934468102d8d9ee>


### Day 93: January 17, 2022

**Today's Progress**: Continuing with the code advents:

Starting part 2 of day 23. At first I thought the code wouldn't need big changes considering Djisktra was successfully implemented for part 1. 

But after doing the changes, the result still isn't the right one :(

I debugged it but still couldn't find where the error is.

**Link to work:** 
- <https://github.com/mathgama/advent-of-code-2021/commit/9cd19efe43754c96f50f3fa213bce4bbd10f0b89>


### Day 94: January 18, 2022

**Today's Progress**: Continuing with the code advents:

After some debugging, I found out that the error was in the way I was transforming the state from an array to a string. It was working for the part 1 because the rooms had only 2 spaces, but with 4 spaces it was causing some bugs.

- [Day 23](https://adventofcode.com/2021/day/23) from the [Advent of Code 2021](https://adventofcode.com/2021/about)

**Link to work:** 
- <https://github.com/mathgama/advent-of-code-2021/commit/08561f2f477f04f513471529c790beca3947fc10>


### Day 95: January 19, 2022

**Today's Progress**: Continuing with the code advents:

I started trying to solve day 24 part 1, but couldn't get too far. This problem actually doesn't involve too much coding, it is more of a "reverse engineering" kind of problem.

I even tried getting some hints on reddit after not being able to do much by myself. But I decided it wasn't fair to get the stars as I couldn't figure out the whole point of the problem by myself (operations with base 26 numbers).

**Link to work:** 
- <https://github.com/mathgama/advent-of-code-2021/commit/c546c64d1c46aa19665b4da35a6d6460874c4f56>


### Day 96: January 20, 2022

**Today's Progress**: Continuing with the code advents:

I started day 25 part 1 and finished it. Pretty straight forward problem!

**Link to work:** 
- <https://github.com/mathgama/advent-of-code-2021/commit/5501237449b507c0f27ea1227d0636f2f202e196>


### Day 97: January 21, 2022

**Today's Progress**: Continuing with the code advents:

As day 25 doesn't really have a part 2 (it just tells you to get all the stars from the other days), I decided to go back to day 12 and try to the 2nd star, as I felt this one was the one I got closer to doing it.

After some debugging and some minor changes to optimize the time, I was able to do it! The program still takes some time to solve it (1-2 minutes?), but this did it for me!

- [Day 12](https://adventofcode.com/2021/day/12) from the [Advent of Code 2021](https://adventofcode.com/2021/about)

So I got a total of 44 stars in 2021 advent of code. As for the rest of the stars, I don't think I'll try to get them as it seemed to out of my knowledge.

![advent-of-code-days](./img/2022-01-21-advent-of-code-days.png)

**Link to work:** 
- <https://github.com/mathgama/advent-of-code-2021/commit/62485ae77d60764a882dd51868018e6703b29d58>


### Day 98: January 22, 2022

**Today's Progress**: For those final 3 days of the "100 days of code challenge" I decided to go back and try to solve some of the SAP Labs Contest that I entered on day 55.

Back on day 55 I found it very difficult to solve those problems, so I decided to try it again and see if I made some progress.

Starting with the problem 'A'. Althought it isn't possible anymore to validate my solution in the Beecrowd (since the contest is over), I'm pretty happy with how easily I was able to solve the examples with the experience I got from the Advent of Code. 

**Link to work:** 
- <https://github.com/mathgama/sap-labs-contest/commit/daaba715dfe7640cdb690aeee443ec32220ffca6>
- <https://github.com/mathgama/sap-labs-contest/commit/b73ec3151d79431db9d6bdd17bbf4123d1713138>


### Day 99: January 23, 2022

**Today's Progress**: Continuing with the SAP Labs problems, I was able to solve the problem 'F' today.

**Link to work:** 
- <https://github.com/mathgama/sap-labs-contest/commit/28fe90fa5996a167cf99139f7a5e80be2ea4dada>
- <https://github.com/mathgama/sap-labs-contest/commit/3da32be75a06f1f13d31b820d5e4647306711b38>


### Day 100: January 24, 2022

**Today's Progress**: Continuing with the SAP Labs problems, I was able to solve the problem 'J' as well.

:tada: :tada: :tada: :tada: :tada: :tada: 

Those 3 last days where so good because I could measure some improvement since day 55 (the first time I tried unsuccessfully to solve those same problems).

I'm pretty happy to finish the 100 days of code challenge! It gets tiring with time, mainly because you can't miss a single day, but it definetely helps a lot on building the habit of studying consistently through pratice! I hope to keep practicing from now on, even though I have finished the challenge.

**Link to work:** 
- <https://github.com/mathgama/sap-labs-contest/commit/776e968d8508c5e763e8ee42f556cdb38c501d24>
- <https://github.com/mathgama/sap-labs-contest/commit/f7c008aada153633f0b059419bb5393d8639845b>