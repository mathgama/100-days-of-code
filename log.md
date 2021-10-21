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
