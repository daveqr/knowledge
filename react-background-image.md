Using require (Webpack Specific):

If you're using Webpack to bundle your assets, you can use the require function to load the image and get the correct URL:

<div
  className="full-background"
  style={{
    backgroundImage: `url(${require('./images/category1.jpg')})`,
    backgroundSize: "cover"
  }}
></div>
>
>
>https://www.freecodecamp.org/news/react-background-image-tutorial-how-to-set-backgroundimage-with-inline-css-style/