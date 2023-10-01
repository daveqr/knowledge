# React

## Set background image

### Using exteranl URL

```
function App() {
  const backgroundImageUrl = "https://example.com/images/category1.jpg";

  const divStyle = {
    backgroundImage: `url(${backgroundImageUrl})`,
  };

  return (
    <div style={divStyle}>
      Hello World
    </div>
  );
}
```

### Using local image

```
import React from "react";
import background from "./images/category1.jpg";

function App() {
  const divStyle = {
    backgroundImage: `url(${background})`,
  };

  return (
    <div style={divStyle}>
      Hello World
    </div>
  );
}

export default App;
```

### Using require

Using Webpack with a local image:

```
<div
  className="full-background"
  style={{
    backgroundImage: `url(${require('./images/category1.jpg')})`,
    backgroundSize: "cover"
  }}
>
Hello World
</div>
```

### Using public image

Images in the `public` directory.

```
<div style={{ backgroundImage: "url(/images/category1.jpg)" }}>
  Hello World
</div>
```