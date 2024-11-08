# interview-toolbox
A collection of notes for interviews

## Forward
After years of doing interviews on both sides, I've found that I enjoy
unrehearsed interviews the most, but I accept that some preparation is good.

These notes help me recall the locations of relevant documentation quickly to
minimize hemming and hawing.

## React
###### `like_button.js`[^1]
```jsx
'use strict';

const { useState } = React;

const e = React.createElement;

function LikeButton() {
  const [liked, setLiked] = useState(false);

  if (liked) {
    return 'You liked this.';
  }

  return (
    <button onClick={() => setLiked(true)}>
      Like
    </button>
  );
}

const domContainer = document.querySelector('#like_button_container');
const root = ReactDOM.createRoot(domContainer);
root.render(e(LikeButton));
```

## License
Content at [legacy.reactjs.org](https://legacy.reactjs.org/) is CC-BY-4.0 licensed, as found in the [LICENSE-DOCS.md](https://github.com/reactjs/legacy.reactjs.org/blob/main/LICENSE-DOCS.md) file.  
Content submitted to [react.dev](https://react.dev/) is CC-BY-4.0 licensed, as found in the [LICENSE-DOCS.md](https://github.com/reactjs/react.dev/blob/main/LICENSE-DOCS.md) file.

[^1]: https://legacy.reactjs.org/docs/add-react-to-a-website.html
